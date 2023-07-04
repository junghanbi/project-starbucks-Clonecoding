# Starbucks Clone Coding

### 완성 사이트
https://xn--clonecodingstarbucks-9u6e.netlify.app/
### 사용한 라이브러리
+ 구글 Font
+ 구글 icon image
+ lodash : 스크롤을 제어할 수 있는 라이브러리
+ gshap : 자바스크립트 애니메이션
+ ScrollMagic : 스크롤에 따라 해당영역 감지
```javascript
// Scroll Magic
const spyEl = document.querySelectorAll('section.scroll-spy');
spyEl.forEach(function(spyEl){
  new ScrollMagic.Scene({
    triggerElement : spyEl, //보여짐 여부를 감지할 요소를 지정
    triggerHook : 0.8,
  })
  // show 넣었다가 뺏다가
  // .setClassToggle(토글할요소,'넣었다 뺄 class 이름')
  .setClassToggle(spyEl,'show')
  .addTo(new ScrollMagic.Controller());
});
```
```CSS
/* scroll Magic으로 연결할 CSS */
/* 맨처음 브라우저 로딩시 안보이게 설정 */
.back-to-position{opacity: 0;transition: all 1s;}

/* 왼쪽 > 오른쪽 등장하는 모션의 시작 위치 */
.back-to-position.to-right{transform: translateX(-150px);}

/* 오른쪽 > 왼쪽 등장하는 모션의 시작 위치 */
.back-to-position.to-left{transform: translateX(150px);}

/* show가 추가가되면 실행할 모션 */
.show .back-to-position{opacity: 1;transform: translateX(0);}
.show .back-to-position.delay-0{transition-delay: 0s;}
.show .back-to-position.delay-1{transition-delay: 0.3s;}
.show .back-to-position.delay-2{transition-delay: 0.6s;}
.show .back-to-position.delay-3{transition-delay: 0.9s;}
```
+ Swiper slider (세로, 가로)
  ```javascript
  //세로 : swiper
  new Swiper(".notice-slide", {
    autoplay: {     //자동슬라이드 (false-비활성화)
      delay: 2500, // 시간 설정
      disableOnInteraction: false, // false-스와이프 후 자동 재생
    },
    loop : true,   // 슬라이드 반복 여부
    direction : 'vertical'
  });



  //가로 : swiper
    new Swiper('.awards .swiper', {
    loop: true,
    slidesPerView: 5, //한번에 보여줄 슬라이드 갯수
    autoplay: {     //자동슬라이드 (false-비활성화)
      delay: 2500, // 시간 설정
    },
    spaceBetween: 30,
    loopAdditionalSlides : 1, 
    // Navigation arrows
    navigation: {
      nextEl: '.awards .swiper-next', //이전버튼
      prevEl: '.awards .swiper-prev', //다음버튼
    },
  });
  
  //promotion 부분 숨겼다 보였다 하는 기능
  const promotionEl = document.querySelector('.promotion');
  const promotionToggleBtn = document.querySelector('.toggle-promotion');
  let isHidePromotion = false; //슬라이드 숨김
  console.log(isHidePromotion);
  
  //토글 버튼
  promotionToggleBtn.addEventListener('click', function(){
    isHidePromotion = !isHidePromotion; //슬라이드 숨김 값을 반대로 할당

    if(isHidePromotion){
      promotionEl.classList.add('hide');
    }else{
      promotionEl.classList.remove('hide');
    }
  });
  ```
