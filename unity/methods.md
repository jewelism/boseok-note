## 메소드와 용어

#### 레이캐스트(Raycast)
 - 광선을 쏴서 지정한 방향과 거리 이내에 부딪히는 게임오브젝트가 있는지 판단하는 알고리즘
#### Distance
 - 두 오브젝트의 거리 구하기
```csharp
float distance1 = Vector3.Distance(transform.position, box.position);
```
#### 자식 게임오브젝트 찾기
```csharp
Transform[] child2 = GameObject.Find("부모이름").GetComponentsInChildren<Transform>();
```
#### Coroutine(코루틴)
 - 쓰레드와 비슷한 개념이지만 차이가 좀 있음.
#### Scene 씬의 전환
빌드&세팅 메뉴에서 add open scenes로 씬을 먼저 등록한다음,
```csharp
Application.LoadLevel("이름");
```
#### PlayerPrefs

간단한 데이터를 저장하고 불러올수있는 클래스

key-value 형식으로 저장한다.
```csharp
PlayerPrefs.SetInt("score", 100);
PlayerPrefs.SetString("name", "developer");
```