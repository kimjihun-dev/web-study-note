# web-study-note
HTML5, CSS3, Javascript, jQuery 관련 정리노트
<br><br>
#### NanumSquare webfont

    [나눔스퀘어웹폰트링크](https://github.com/moonspam/NanumSquare)
    
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
    <div class="tab-1" class="tab-content current">Menu01 contents</div>
    <div class="tab-2" class="tab-content">Menu02 contents</div>
    <div class="tab-3" class="tab-content">Menu03 contents</div>
```

<br>

```javascript
    $("ul.tabs li").click(function(){
        const tab_id = $(this).attr("data-tab");
        $("ul.tabs li").removeClass("current");
        $(".tab-content").removeClass("current");
        $(this).addClass("current");
        $("#"+tab_id).addClass("current");
    });
```

<br>


