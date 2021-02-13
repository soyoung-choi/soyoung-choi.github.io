---
layout: post
title: "입력 양식 이벤트"
date: "2021-02-13"
categories: jQuery
---

&nbsp;

이벤트 이름 | 설명
|:---:|:---:|
change | 입력 양식의 내용이 변경될 때 발생
focus | 입력 양식에 초점이 맞춰질 때 발생
focusin | 입력 양식에 초점이 맞추어지기 바로 전에 발생
focusout | 입력 양식에 초점이 사라지기 바로 전에 발생
blur | 입력 양식에 초점이 사라지면 발생
select | 입력 양식을 선택할 때 발생 (input[type="text] 태그 및 textarea 태그 제외)
submit | submit 버튼 클릭시 발생
reset | reset 버튼 클릭시 발생

&nbsp;

```html
<body>
  <form id="input-form">
    <table>
      <tr>
        <td>이름</td>
        <td>
          <input type="text" id="name" />
        </td>
      </tr>
      <tr>
        <td>비밀번호</td>
        <td>
          <input type="password" id="password" />
        </td>
      </tr>
    </table>
    <input type="submit" value="제출" />
  </form>
</body>

<script>
  $(document).ready(function() {
    $('#input-form').submit(function(event) {
      // 입력 양식의 value 값 가져오기
      var name = $('#name').val();
      var password = $('#password').val();

      alert(name + ':' + password); // 출력

      event.preventDefault(); // 기본 이벤트 제거
    })
  });
</script>
```

입력 양식의 유효성 검사를 할 때는 **기본 이벤트를 제거**해야 됨

&nbsp;

```html
<body>
  <input type="checkbox" id="all-check" />
  <label>전체선택</label>

  <div id="check-item">
    <input type="checkbox" />
    <label>A option</label>
    <input type="checkbox" />
    <label>B option</label>
    <input type="checkbox" />
    <label>C option</label>
  </div>
</body>

<script>
  $(document).ready(function() {
    $('#all-check').change(function() {
      if(this.checked) {
        $('#check-item').children().prop('checked', true);
      } else {
        $('#check-item').children().prop('checked', false);
      }
    })
  });
</script>
```

체크 상태를 확인할 때는 입력 객체의 checked 속성을 확인한 후, 체크 상태를 변경하고 싶다면 prop() 메서드를 사용

&nbsp;

## ES6 문법 사용할 때 주의할 점

```html
<body>
  <h1>안녕하세요!</h1>
</body>

<script>
  $(document).ready(function() {
    $('h1').click(()=> {
      $(this).css('color', 'red');
    })
  });
</script>
```

**jQuery 이벤트 핸들러로 화살표 함수를 사용하면 this 키워드로 자기 자신을 나타낼 수 없음**

```html
<body>
  <h1>안녕하세요!</h1>
</body>

<script>
  $(document).ready(function() {
    $('h1').click((event)=> {
      $(event.currentTarget).css('color', 'yellow');
    })
  });
</script>
```

**화살표 함수를 사용할 때는 event.currentTarget 속성을 사용**