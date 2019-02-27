## nodejs에서 dynamodb 사용하기


### 환경설정

ubuntu18 기준으로 작성하였습니다.

```bash
sudo apt install awscli
```

```bash
aws configure
```

실행하면 아래처럼 input이 차례대로 4개 나옵니다.

aws계정을 참고해서 복붙하세요~ 아래는 예시입니다.

```bash
AWS Access Key ID [None]: someAccessKey
AWS Secret Access Key [None]: someSecretKey
Default region name [None]: ap-northeast-2
Default output format [None]: json
```

이렇게하면 aws cli는 끝입니다.

노드에서 aws-sdk를 사용할때, 방금 설정한 configure를 사용하게 됩니다.

노드 프로젝트에서 아래 명령어를 실행합니다.

```bash
npm install aws-sdk -S
```

------------------------

### 테이블 생성

```js
// config/dynamo.js
const {AWS_REGION} = require('../../constants');

const AWS = require('aws-sdk');

AWS.config.update({
  region: AWS_REGION,
});

const docClient = new AWS.DynamoDB.DocumentClient();

module.exports = {AWS, docClient};
```

```js
// constants/index.js
const AWS_REGION = 'ap-northeast-2';
const SURVEY_TABLE = 'moqa_web_survey';

module.exports = {AWS_REGION, SURVEY_TABLE};
```

```js
// scripts/createSurveyTable.js
const {AWS} = require('../../config/dynamo');

const {SURVEY_TABLE} = require("../../../constants");

const dynamodb = new AWS.DynamoDB();

const params = {
  TableName: SURVEY_TABLE,
  KeySchema: [
    {AttributeName: '_id', KeyType: 'HASH'},
  ],
  AttributeDefinitions: [
    {AttributeName: '_id', AttributeType: 'S'},
  ],
  ProvisionedThroughput: {
    ReadCapacityUnits: 10,
    WriteCapacityUnits: 10
  }
};

dynamodb.createTable(params, function (err, data) {
  if (err) {
    console.error('Unable to create table. Error JSON:', JSON.stringify(err, null, 2));
  } else {
    console.log('Created table. Table description JSON:', JSON.stringify(data, null, 2));
  }
});
```

코드를 작성하고, 아래 명령어를 실행시킵니다.

```bash
node scripts/createSurveyTable.js
```

테이블이름 같은 경우는, get post put delete할때도 써야하므로 별도의 constants.js에서 관리합니다.

---------------------

## 테이블에서 데이터 조회

```js
const findAll = () => {
  return new Promise((resolve, reject) => {
    const params = {
      TableName: SURVEY_TABLE,
    };

    docClient.scan(params, function (err, data) {
      if (err) {
        console.error("Unable to read item. Error JSON:", JSON.stringify(err, null, 2));
        const {message, time} = err;
        reject({message, time});
      } else {
        resolve(data.Items);
      }
    });
  });
};
```

위 코드 블럭은 해당 테이블의 <b>모든 데이터</b>를 조회하는 function입니다.

express사용시, 라우팅은 위의 함수를 활용하여 아래와 같이 작성합니다.

```js
router.get('/all', async (req, res, next) => {
  findAll().then(data => {
    res.status(200).send(data);
  }).catch(e => {
    res.status(500).send(e);
  });
});
```

모두 조회 후 author로 필터링

```js
router.get('/author/:author', async (req, res, next) => {
  const {author} = req.params;

  findAll().then(data => {
    const result = data.Items.filter(item => item.author === author);
    res.status(200).send(result);
  }).catch(e => {
    res.status(500).send(e);
  });
});
```

_id로 한개 조회하기

```js
router.get('/:_id', async (req, res, next) => {
  const {_id} = req.params;

  const params = {
    TableName: SURVEY_TABLE,
    Key: {_id}
  };

  docClient.get(params, function (err, data) {
    if (err) {
      const {message, time} = err;
      res.status(500).send({message, time});
      console.error("Unable to read item. Error JSON:", JSON.stringify(err, null, 2));
    } else {
      res.status(200).send(data.Item);
    }
  });
});
```

docClient의 scan메소드와는 다르게, get을 사용하면 key로 설정해놓은 컬럼들을 params의 Key라는 프로퍼티에 할당해야합니다.

sort key가 있다면, sort key도 넣어야합니다.

-----------------------

ref: https://docs.aws.amazon.com/ko_kr/amazondynamodb/latest/developerguide/GettingStarted.NodeJs.html