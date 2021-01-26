---
layout: post
title: "addClass()와 removeClass() 함수를 이용한 색상 변환 애니메이션 구현"
date: "2021-01-24"
categories: jQuery
---

div 태그에 hover를 하게 되면 클래스가 추가 및 제거되는 것을 볼 수 있다.  
각 메서드의 첫 번째 매개변수에는 **클래스명**을 지정하고, 두 번째 매개변수에는 **애니메이션 적용 속도**를 입력하면 잘 작동하게 된다.

```html
<style>
  .reverse {
    color: white;
    background-color: black;
  }
</style>

<body>
  <div>
    <h1>바껴라 얍!</h1>
  </div>
</body>

<script>
  $(document).ready(function() {
    $('div').hover(function() {
      $(this).addClass('reverse', 1000);
    }, function() {
      $(this).removeClass('reverse', 1000);
    });
  });
</script>
```
