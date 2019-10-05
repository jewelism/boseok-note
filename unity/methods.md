# methods

### 레이캐스트\(Raycast\)

* 광선을 쏴서 지정한 방향과 거리 이내에 부딪히는 게임오브젝트가 있는지 판단하는 알고리즘

  **Distance**

* 두 오브젝트의 거리 구하기

  ```csharp
  float distance1 = Vector3.Distance(transform.position, box.position);
  ```

  **자식 게임오브젝트 찾기**

  ```csharp
  Transform[] child2 = GameObject.Find("부모이름").GetComponentsInChildren<Transform>();
  ```

  **Coroutine\(코루틴\)**

* 쓰레드와 비슷한 개념이지만 차이가 좀 있음.

  **Scene 씬의 전환**

  빌드&세팅 메뉴에서 add open scenes로 씬을 먼저 등록한다음,

  ```csharp
  Application.LoadLevel("이름");
  ```

  **PlayerPrefs**

간단한 데이터를 저장하고 불러올수있는 클래스

key-value 형식으로 저장한다.

```csharp
PlayerPrefs.SetInt("score", 100);
PlayerPrefs.SetString("name", "developer");
```

## 자주 사용하는 메소드

```csharp
Camera.main.ScreenToWorldPoint(Input.mousePosition)
```

화면 상에서 마우스의 위치이다. Input.mousePosition을 메인 카메라가 본 시점에서의 위치.

```csharp
Instantiate(생성물, 위치, 회전)
```

오브젝트 생성 함수.

```csharp
Input.GetKey(keycode)
```

키 눌렀을 때 입력 확인

```csharp
Input.GetMouseButtonDown()
```

0은 왼쪽, 1은 오른쪽, 2는 휠.

