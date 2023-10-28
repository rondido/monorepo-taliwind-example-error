## monorepo로 작업중인 프로젝트에서 일어난 error들을 재현해보고 해결하는 과정 다시 한번 거치는 repo

### 목차

---

### 1번

- component에서 header라는 component를 tailwind와 Nextui를 통해 생성 후 service에서 사용하는 상황

- component에서 직접적으로 사용하였을때는 tailwind와 Nextui가 정상적으로 작동하였지만 service repo에서 component를 불러와 사용하는 순간부터는 tailwind가 브라우저에서 적용되었다가 안되었다가 하는 현상 발생

## 회고

### 1번

처음 error를 만났을 때는 tailwind를 적용하는 과정에서 적용이 되었다가 안되었다가 하는 것을 보고 존재하지 않는 컨벤션을 사용한 것이거나 부모의 기준을 가지고 css가 적용되는 내용이 있을 수 있으니 처음부터 차근차근 다시 해보면서 문제점을 찾아보고자 노력하였다.

tailwind에 사용하는 rem단위가 아닌 px 단위 등에 대해서 알게 되었고 이를 직접 적용해보면서 component에서는 잘 적용되었지만 service에서는 적용되지 않는 것을 보고 nextui와 tailwind의 호환성이나 여러 버그로 인한 문제이지 않을까라는 생각을 하게 되었고, 스터디 커뮤니티를 통해 다른 스티디원에게 자문을 구해 같이 코드를 하나하나 뜯어보았지만 근본적인 원인을 찾지 못했다.

그리하여, nextui를 대체 할 수 있는 mui나 ant-design으로 바꾸고자 프로젝트 팀원과 상의를 하였다. 근데 상의하는 과정에서 tailwind setting이 잘못된거 아니냐는 이야기를 듣게 되었고, 이를 토대로 config관련 setting을 찾아보게되었다.

결국 혼자서 해결하지 못했고, 팀원과 함께 해결하는 도중, 근본적인 문제가 monorepo로 인한 문제일 수 있다는 생각을 하게 되었고 github issue에서 tailwind monorepo 관련 error issue를 찾을 수 있게 되었다.

https://github.com/tailwindlabs/tailwindcss/issues/3277
