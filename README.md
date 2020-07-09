# web-study-note
HTML5, CSS3, Javascript, jQuery 관련 정리노트
<br><br>
**jquery accordion 아코디언 구현**
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
##### jquery side nav 구현




