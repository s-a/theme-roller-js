theme-roller-js
====================

This JavaScript library is used by the [deep-js](https://github.com/s-a/deep-js) [Theme Roller package](https://github.com/s-a/deep-js-theme-roller).

[Online demo](http://app.deep-js.com/#theme-roller/index)

### Html skeleton
```html
<style>
  .style-selector-item:hover{
    background-color: #333;
    color: ghostwhite!important;
  }

  #sheet-colors{
    position: fixed;
    right: 0;
    top: 43px;
    z-index: 3000;
    border: solid 11px #333;
    border-radius: 11px;
    background-color: white;
  }

  .style-selector-item{
    border-bottom: solid 1px #333;
    padding: 3px;
  }
  #sheet-colors-header{
    width: 100%;
  }

  #sheet-colors-content{
    overflow: auto;
    max-height: 300px;
  }

  #sheet-colors-header, #sheet-colors-content{
    padding: 6px;
  }
  .theme-roller-style-container{
    text-overflow: ellipsis;
    width: inherit;
    white-space: nowrap;
    overflow: hidden;
    font-size: 80%;
  }
</style>



<div class="hero-unit visible-phone">
  <h1>{{_ "Sorry"}}!</h1>
  <p>{{_ "The Theme Roller is not good to handle on small devices."}}</p>
</div>

<div id="sheet-colors" class="span6 hidden-phone">
  <div id="sheet-colors-header">
    <div id="sheet-colors-header-title"class="muted" title="deep-js Theme Roller">Roller</div>
    <div class="nav-bar nar-bar-header">
      <a class="btn btn-mini minimize" href="#">{{_ "Minimize"}}</a>
      <a class="btn btn-mini disabled load" href="#">{{_ "load"}}</a>
      <a class="btn btn-mini disabled save" href="#">{{_ "Save"}}</a>
      <a class="btn btn-mini disabled share" href="#">{{_ "Share"}}</a>
      <a class="btn btn-mini disabled reset" href="#">{{_ "Reset"}}</a>
      <a class="btn btn-mini help" href="#">{{_ "Help"}}</a>
    </div>
  </div>
  <div id="sheet-colors-content" class="well">
    <h5>{{_ "intro__text__a"}}</h5>
    {{_ "intro__text__b"}}
    <i class="alert-info">{{_ "intro__text__c"}}</i>
  </div>
</div>
```

### Html skeleton

```javascript
  ThemeRoller.init($("#sheet-colors")), {
    "translate" : Deep.translate,   // optional - custom translation method.
    "error": function(userValue) {  // optional custom error method.
      Deep.Web.UI.msg({type: "error", msg: Deep.translate("invalid__color__value", userValue )});
    }
  });
  Deep.on("sa.theme-roller.index.render", function(){
    var watchElements = $("body").find("*:not(#sheet-colors):not(#sheet-colors *)");
    ThemeRoller.listen(watchElements);
  });
```