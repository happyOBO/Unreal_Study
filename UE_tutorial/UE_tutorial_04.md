## Unreal tutorial-4

- 해당 내용은 아래의 영상들을 바탕으로 만들었습니다. 
    - [Unreal tutorial 04](https://youtu.be/D4wJ_YO8ZWM)
    - [Unreal tutorial 05](https://youtu.be/5YooEu-ktww) 
    - [Unreal tutorial 06](https://youtu.be/9nMnQE-Zg-o) 
    - [Unreal tutorial 07](https://youtu.be/EmvekeKk-0o) 

- 리눅스에서 진행하고 있습니다.
- **목표**
    1. 블루프린트 클래스로 조명을 생성한다.
    2. 해당 조명에 가까이 가면 불이 켜진다.
    3. 해당 조명에 가까이 가면 특정한 키보드 키를 눌렀을 때 불이 켜진다.


### 진행 순서

1. 먼저 이전 포스트에서 작성한 레벨을 그대로 사용할 것이다. 이전 처럼 레벨 블루프린트를 사용하지 않고 블루 프린트 클래스를 작성해서 만들면 어떤점이 좋은가?
    - 재사용이 용이하다.
    - 만약에 여러 방이 존재하고, 방마다 출입시에 조명이 껐다가 켜져야하는 상황이라면
    - 레벨 블루프린트로 하나하나 만들기에는 무리가 있다.
    - 클래스를 사용한다면 생성한 액터를 계속해서 복사 붙여넣기 할 수있다.
2. 따라서, 이전에 사용했던 레벨 블루 프린트를 끊어 놓자. ``Break Link to Delay``를 통해 `delay` 노드와의 간선을 끊을 수 있다.

    <img src="./assets/tut04/1.png" width="600">

3. `Contents` 탭에서 새 폴더를 생성하자. 

    <img src="./assets/tut04/2.png" width="600">

4. 새로 만든 폴더에 우 클릭해서 ``Blueprint Class``를 하나 생성하자. 이름은 ``Light_BP``로 한다.

    <img src="./assets/tut04/3.png" width="600">

5. 클래스를 생성하려면 부모 클래스를 지정해야한다. ``Actor`` 클래스를 생성하자. 액터 클래스는 월드에서 오브젝트를 놓거나 생성할 수 있다.

    <img src="./assets/tut04/5.png" width="600">

6. 아래와 같이 클래스가 하나 생긴것을 볼 수 있다.

    <img src="./assets/tut04/4.png" width="600">

7. 해당 파일을 더블클릭하면 아래와 같은 창이 뜬다.

    <img src="./assets/tut04/7.png" width="600">

8. 레벨 창에 가서 ``Contents> StarterContent> Props`` 에서 해당 조명을 드래그해서 뷰포트에 놓는다.

    <img src="./assets/tut04/8.png" width="600">

    <img src="./assets/tut04/9.png" width="600">

9. ``Add Component`` 탭에 가서 ``spot light``를 드래그 해서 놓는다.

    <img src="./assets/tut04/10.png" width="300">
    <img src="./assets/tut04/11.png" width="600">
    <img src="./assets/tut04/12.png" width="600">

10. 레벨 창에 가서 ``Light_BP`` 를 레벨 창에 드래그해서 원하는 위치에 놓는다.

    <img src="./assets/tut04/13.png" width="600">
    <img src="./assets/tut04/14.png" width="600">

11. 이동, 회전을 통해 조명 방향을 편집한다.

    <img src="./assets/tut04/15.png" width="600">

12. 조명 상세 탭에 가서 `Light Color` , ``Cone Angle``(조명 반경)등을 조정한다.
    
    <img src="./assets/tut04/16.png" width="600">
    
    <img src="./assets/tut04/17.png" width="600">

13. 알맞게 조정하면 다음과 같이 나타난다.~~조명 방향은 위로하고, 조명 색깔은 금색으로~~

    <img src="./assets/tut04/18.png" width="600">

14. `Conponents` 검색 창에 ``Box collision``을 검색해서 추가한다.

    <img src="./assets/tut04/19.png" width="600">

15. 사용자의 캐릭터가 들어가서 반응할 수있을 만큼 크기를 조절한다.

    <img src="./assets/tut04/20.png" width="600">
    <img src="./assets/tut04/21.png" width="600">

16. 마찬가지로, `Conponents` 검색 창에 ``text``을 검색해서 추가한다. 텍스트 상세탭에서 글자 크기, 내용을 편집 할 수 있다.

    <img src="./assets/tut04/22.png" width="600">

17. ``Component`` 탭에서 ``spot light``를 드래그해서 뷰포트에 가져온다.

    <img src="./assets/tut04/24.png" width="600">

18. 화살표 선을 따서 ``Toggle visibility``를 가져온다. ~~불을 껐다 켤수 있는 노드~~ 

    <img src="./assets/tut04/25.png" width="600">

19. ``Box`` 컴포넌트를 클릭한채로 뷰포트를 우클릭하여 ``On Component Begin Overlap`` 노드를 가져온다.

    <img src="./assets/tut04/26.png" width="600">

20. 위와 같이 ``On Component End Overlap`` 노드를 가져와서 아래와 같이 연결한다.

    <img src="./assets/tut04/31.png" width="600">

21. 레벨을 실행해보면 다음과같이 뜬다.

    <img src="./assets/tut04/27.png" width="600">

22. 가까이 가면 조명이 켜지는것을 볼수 있다.

    <img src="./assets/tut04/28.png" width="600">

23. **클래스의 장점**!! 해당 조명을 복사 붙여넣기 하면 아래와 같이 여러개를 만들어 낼 수 있다.

    <img src="./assets/tut04/29.png" width="600">
    <img src="./assets/tut04/30.png" width="600">

24. 이제 키보드 입력을 했을 때만 조명이 켜지게끔 한다. ``Enable input``노드를 통해 키보드 입력을 활성화 시킨다. (박스에 들어 왔을 때)

    <img src="./assets/tut04/32.png" width="600">

25. 그리고 플레이어의 컨트롤러를 얻는 노드를 연결한다.

    <img src="./assets/tut04/33.png" width="600">

26. 박스에 벗어 났을 때는 키보드 키 입력을 비활성화 시키자.

    <img src="./assets/tut04/34.png" width="600">

27. 아래와 같이 연결하면 플레이어 컨트롤러를 두개 중복을 안시켜도 된다.

    <img src="./assets/tut04/35.png" width="600">

28. 키보드 키중 ``F`` 에 조명이 켜지도록 노드를 아래와 같이 설정한다.

    <img src="./assets/tut04/36.png" width="600">




29. 텍스트도 가까이 가면 보이고, 멀리가면 보이지 않게끔 설정하자. 아래와 같이 만들수 있다.

    <img src="./assets/tut04/41.png" width="600">

30. 더 간단하게 만들 수 있다.

    <img src="./assets/tut04/42.png" width="600">

31. 실행 화면은 다음과 같다.

    <img src="./assets/tut04/38.png" width="600">
    <img src="./assets/tut04/39.png" width="600">
    <img src="./assets/tut04/40.png" width="600">

32. 부분 선택을 한 후에 `C` 를 누르면 그룹화를 할 수 있다.

    <img src="./assets/tut04/43.png" width="600">

33. 그룹 색깔도 여러가지로 바꿀 수 있다.

    <img src="./assets/tut04/44.png" width="600">