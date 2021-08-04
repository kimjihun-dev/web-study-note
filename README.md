# web-study-note
HTML5, CSS3, Javascript, jQuery 관련 정리노트
<br><br>
#### NanumSquare webfont
    
[나눔스퀘어웹폰트링크](https://github.com/moonspam/NanumSquare)

link 방식(권장)

```css
<link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/gh/moonspam/NanumSquare@1.0/nanumsquare.css">
```

import 방식

```css
@import url(https://cdn.jsdelivr.net/gh/moonspam/NanumSquare@1.0/nanumsquare.css);
```

적용

```css
body		{ font-family: 'NanumSquare', sans-serif; }
.normal		{ font-weight: 400 }
.bold		{ font-weight: 700 }
.bolder		{ font-weight: 800 }
.light		{ font-weight: 300 }
```

<br>

### 이롭게 바탕체 웹폰트 적용하기

import 방식

```css
@import url('//cdn.jsdelivr.net/font-iropke-batang/1.2/font-iropke-batang.css');
body { font-family: 'Iropke Batang', serif; }
```

<br>

#### jquery accordion 아코디언 구현
<br>

```javascript
    $(document).ready(function(){
      // 클릭해서 보여줄 요소를 숨김
      $("ul").hide();
      // 메뉴 클릭시 
      $("accordion > a").click(function(){
        // 메뉴의 다음요소에 해당되는 요소, 위에서 숨겨놨던 부분을 슬라이다운으로 보여준다.
        $(this).next().slideDown("slow");    
        // 현재 클릭된 요소가 아니라면 다른 메뉴들은 슬라이드업으로 닫아준다.
        $(".accordion > a").not(this).next().slideUp("slow");
      });
    });
``` 
<br>
```javascript
    또 다른 방법
    $(document).ready(function(){
        // 기본적으로 다 숨김상태
        $(".depth-2").hide()
        // 메뉴 클릭시
        $(".menu").click(function (){
			// 메뉴 클릭시 하위메뉴들이 나오게 한다.
            // 내가 클릭한 메뉴의 하위 메뉴들이 아니면 슬라이드업으로 올려버리고
            // 내가 클릭한것이면 슬라이드로 내려오게 한다.
			$(".depth-2").not($(this).next(".m-depth-2").slideToggle(500)).slideUp();
		});
    });
```

<br><br>
#### jquery side nav 구현
<br>

```javascript
    $(allBtn).click(function(){
        // 보여줘야 될 div 는 미리 left -320px 라는 옵션을 줘서 화면에서 숨겨준다.
        // 버튼 클릭시 left 값 0을 줘서 나타나게 한다.
        $("#sideNav").animate({left: "0px"}, 300);
    });
    $(closeBtn).click(function(){
        // 다시 마이너스 옵션을 줘서 닫기 버튼클릭시 화면에서 숨긴다.
        $("#sideNav").animate({left: "-320px"}, 300);
    });
```
<br><br>
#### jquery dropDown menu 구현 (개선필요)
<br>

```javascript
    // 만들어놓은 드랍메뉴는 일단 숨긴다.
    $(".dropMenu").hide();
    // 드랍메뉴를 나타낼 버튼을 클릭하면
    $(moreBtn).click(function(){
        // 만약 아무것도 없는 상태라면
        if($(".dropMenu").css("display") == "none") {
            // 드랍메뉴를 보여주고
            $(".dropMenu").show();
        // 드랍메뉴가 있는 상태라면
        } else {
            // 다시 숨긴다.
            $(".dropMenu").hide();
        }
    });
    
    // fadeToggle 를 이용
    $(".gnb .m").hover(function(){
        // 풀다운 메뉴에 사용
        // 메뉴에 마우스오버시 해당되는 요소안에 div 를 찾아 보여준다.
        // Toggle 는 in out 이 다 되는 태그
        $(this).find("div").stop().fadeToggle(200);
    });
```
<br><br>
#### jquery scrollTop 구현
<br>

```javascript
    $(window).scroll(function(){
        if($(this).scrollTop() > 500) {
            $("#topBtn").fadeIn();
        } else {
            $("#topBtn").fadeOut();
        }
    });

    $("#topBtn").click(function(){
        $("html, body").animate({
            scrollTop: 0
        }, 400);
        return false;
    });
```
<br><br>
#### jquery navtigation 구현(작성중)
<br>

```javascript
    $(".gnb4 h2").mouseover(function(){
      $("#header4").stop().animate({ height:"240px" });
     });
     $("#header4").mouseleave(function(){
          $("#header4").stop().animate({ height:"80px" });
     }); 
```
<br><br>
#### ScrollTrigger 구현하기 (스크롤다운시 요소들이 부드럽게 올라오는 효과)
<br>

    필요파일
    
    1. ScrollTrigger.min.js
    2. animations.css  // 효과를 줄 대상에 transition, tramsform 를 정의.
<br>    

```css
<ul data-scroll="toggle(.fromBottomIn, .fromBottomOut)">  // 적용대상에 data-scroll 를 넣는다.
```
<br>
    옵션들
    
    data-scroll="toggle(.fromTopIn, .fromTopOut)"
    data-scroll="toggle(.fromBottomIn, .fromBottomOut)"
    data-scroll="toggle(.fromLeftIn, .fromLeftOut)"
    data-scroll="toggle(.fromRightIn, .fromRightOut)"
    data-scroll="toggle(.scaleDownIn, .scaleDownOut)"
    
<br>

```javascript
// 코드 하단에 아래의 스크립트 첨부
document.addEventListener('DOMContentLoaded', function () {
  var trigger = new ScrollTrigger({
  addHeight: true
 });
});
```
<br><br>
#### jQuery 로 구현하는 Tab Menu
<br>

```css
    <ul class="tabs">
        <li class="tab-link current" data-tab="tab-1">Menu01</li>
        <li class="tab-link" data-tab="tab-2">Menu02</li>
        <li class="tab-link" data-tab="tab-3">Menu03</li>
    </ul>
    <div id="tab-1" class="tab-content current">Menu01 contents</div>
    <div id="tab-2" class="tab-content">Menu02 contents</div>
    <div id="tab-3" class="tab-content">Menu03 contents</div>
```

<br>

```css
    // 메뉴를 클릭할시 나타내는 컨텐츠들은 기본으로 display none으로 설정
    .tab-content { display: none; }
    // 스크립트 구문에서 클릭시 다시 나타낸다.
    .tab-content.current { display: block; }
```

<br>

```javascript
    $("ul.tabs .tab-link").click(function(){
        const tab_id = $(this).attr("data-tab");
        $(".tab-link").removeClass("current");
        $(".tab-content").removeClass("current");
        $(this).addClass("current");
        $("#"+tab_id).addClass("current");
    });
```

<br><br>
#### 모바일 버튼 클릭시 어두운 배경화면 만들기
<br>

```html
    // div 개체 두개를 만들어 하나는 전체메뉴 하나는 배경이미지로 지정
    <div class="moblie_wrap"></div>
    <div class="mobile_bg"></div>
```

<br>

```css
    // 어두운 배경
    display: block;
    position: fixed;
    top: 0px;
    left: 0px;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    z-index: 1050;
```



