---
layout: post
published: true
title: input text 중 일부만 마스킹처리
date: '2020-05-01'
tags: [input, masking]
---

프론트엔드 개발을 하다보면 보안상의 이유로 input 필드에 입력한 내용 중 일부를 마스킹처리해서 보여줘야하는 기능을 요구할 때가 있다.  

- 화면에 보여질때만 일부 마스킹된 입력값만 보이고 input 필드를 수정하기위하여 선택했을때엔 마스킹처리가 안된 원래 input 값이 보인다.
- input이 끝나면 다시 마스킹처리가 된 값이 보인다.  
- 실제로 시스템에서 입력받은 값은 마스킹처리가 안된 유저가 입력한 값이 저장된다.

좀 더 깔끔한 구현이 가능하겠지만 프론트엔드 개발을 경험이 부족해서 순수 html과 javascript 를 사용한 구현을 하였다.
<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="js,result" data-user="redrebel" data-slug-hash="gOaxOZm" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="gOaxOZm">
  <span>See the Pen <a href="https://codepen.io/redrebel/pen/gOaxOZm">
  gOaxOZm</a> by Junggeun Lee (<a href="https://codepen.io/redrebel">@redrebel</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

주요 내용은 input 필드를 2개(maskedId, id)를 만들어서 id input 필드의 type은 hidden으로 처리한다. (예제에서는 확인을 위하여 hidden 처리를 하지 않았다.)

- maskedId input 필드를 선택(onfocus)하면 id input 필드의 값을 보여준다
- 입력을 마치고 maskedId input 필드를 나가게(onblur) 되면 javascript function(make_mask_id)를 호출하여 maskedId input 필드에 앞에 4자가 마스킹처리가된 값을 value로 지정하고, id input 필드에 입력받은 값을 value로 저장한다.
