---
layout: post
title: "키보드 이벤트"
date: "2021-02-13"
categories: jQuery
---

키보드 이벤트를 사용하여 동적으로 글자 수를 세는 방법에 대해서 알아보기.

&nbsp;

이벤트 이름 | 설명
|:---:|:---:|
keydown | 키보드를 누를 때 발생
keypress | 글자가 입력될 때 발생
keyup | 키보드를 땔 때 발생

&nbsp;

```html
<body>
  <h1>메모장</h1>
  <textarea cols="70" rows="5"></textarea>
  <p>
    <span class="remain">150</span>
    <span>자 남았습니다.</span>
  </p>
</body>

<script>
  $(document).ready(function() {
    $('textarea').keyup(function() {
      // 남은 글자수 구하기
      var input_length = $('textarea').val().length;
      var remain = 150 - input_length;

      // 문서 객체에 입력
      $('.remain').html(remain);
      
      // 문서 객체의 색상 변경
      if(remain >= 0) {
        $('.remain').css('color', 'black');
      } else {
        // 글자 수 초과
        $('.remain').css('color', 'red');
      }
    })
  })
</script>
```

&nbsp;

## 키보드 이벤트 순서

1. 사용자가 키보드를 누른다.
2. keydown 이벤트가 발생된다.
3. 글자가 입력된다.
4. keypress 이벤트가 발생된다.
5. 사용자가 키보드에서 손을 떈다.
6. keyup 이벤트가 발생된다.

&nbsp;

## keyup 이벤트를 사용하는 이유

영어를 입력하면 keypress 이벤트를 사용하겠지만, 한글은 keypress 이벤트를 지원하지 않기 때문에 keypress 이벤트는 배제한다.
또한, keydown 이벤트가 발생한 순간에는 글자가 완전히 입력되어 있지 않기 때문에 입력한 글자수를 표시하려면 keyup 이벤트를 사용해야 한다.
