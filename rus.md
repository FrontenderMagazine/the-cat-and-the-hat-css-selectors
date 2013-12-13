«Котик» и «Домик» — новые CSS‑селекторы
==========================================================

Один из самых сложных аспектов использования CSS, инкапсулированного в теневом 
дереве — это определение того, что именно наследуется из CSS 
родительского документа. Изначально предполагалось, что разработчики будут сами
определять элементы, которые наследуют CSS родительского документа 
[с помощью атрибута `part`][1], но этот метод оказался недостаточно гибким.
Сейчас считается, что границы теневого дерева должны предотвращать *ненамеренную* 
стилизацию элементов, которые она содержит, и допускать осознанную. 
И это как раз тот самый момент, когда вам могут пригодится новые CSS-селекторы «котик» и «домик».

## Поддержка

Если вы хотите попробовать примеры, вам нужен [Chrome Canary][3]
версии 33 и выше.

Также убедитесь, что у вас включены **экспериментальные функции веб-платформы** 
(Experimental Web Platform features) на внутренней странице настроек хрома `chrome://flags`.

## «Домик»

Селектор «Домик», он же одиночный циркумфлекс ( `^` ), позволит применить стили, 
заданные в родительском документе к элементам, которые находятся на верхнем 
уровне теневого дерева. Если вы работаете с элементом, у которого есть только один 
корневой узел теневого дерева, вы можете стилизовать любой его дочерний элемент, 
используя селектор «Домик».

<div data-height="240" data-theme-id="3073" data-slug-hash="uvkjb" data-user="matmuchrapna" data-default-tab="css" class='codepen'><pre><code>&#x2F;* Замечание: работает только в Chrome Canary. *&#x2F;
&#x2F;* Включите экспериментальные функции веб-платформы *&#x2F;
&#x2F;* на странице настроек chrome:&#x2F;&#x2F;flags *&#x2F;

&#x2F;* «Домик» применяет стили, заданные в родительском *&#x2F;
&#x2F;* документе, к элементам из верхнего уровня теневого дерева *&#x2F;
x-foo ^ h2 {
  color: red;
}</code></pre>
<p>See the Pen <a href='http://codepen.io/matmuchrapna/pen/uvkjb'>«Домик»  — новый CSS-селектор</a> by Vladimir Starkov (<a href='http://codepen.io/matmuchrapna'>@matmuchrapna</a>) on <a href='http://codepen.io'>CodePen</a></p>
</div><script async src="//codepen.io/assets/embed/ei.js"></script>


## «Котик»

Селектор «Котик», двойной циркумфлекс ( `^^` ), намного мощнее. Он позволяет
проникать на любое количество уровней в глубину теневого дерева. Поэтому, если у вас
есть одна теневая модель внутри другой (так часто бывает, когда используются вложенные элементы, 
содержащие теневую модель), вы сможете оформить все элементы разом.

<div data-height="366" data-theme-id="3073" data-slug-hash="qfvLB" data-user="matmuchrapna" data-default-tab="css" class='codepen'><pre><code>&#x2F;* Замечание: работает только в Chrome Canary. *&#x2F;
&#x2F;* Включите экспериментальные функции веб-платформы *&#x2F;
&#x2F;* на странице настроек chrome:&#x2F;&#x2F;flags *&#x2F;

&#x2F;* «Домик» применяет стили, заданные в родительском *&#x2F;
&#x2F;* документе, к элементам из верхнего уровня теневого дерева *&#x2F;
x-foo ^ h2 {
  color: red;
}

&#x2F;* «Котик» применяет стили, заданные в родительском *&#x2F;
&#x2F;* документе, к элементам на всех уровнях теневого дерева *&#x2F;
x-foo ^^ h2 {
  font-family: Courier;
}</code></pre>
<p>See the Pen <a href='http://codepen.io/matmuchrapna/pen/qfvLB'>«Котик» — новый CSS‑селектор</a> by Vladimir Starkov (<a href='http://codepen.io/matmuchrapna'>@matmuchrapna</a>) on <a href='http://codepen.io'>CodePen</a></p>
</div><script async src="//codepen.io/assets/embed/ei.js"></script>


## Стилизация нативных элементов

[@Volker_E спросил][8] могут ли селекторы `^` и `^^` быть использованы для
стилизации нативных элементов таких, как, например, `<video>`. Как оказалось, 
данные селекторы это умеют, что не может не радовать.

<div data-height="215" data-theme-id="3073" data-slug-hash="Jibjz" data-user="matmuchrapna" data-default-tab="css" class='codepen'><pre><code>&#x2F;* Замечание: работает только в Chrome Canary. *&#x2F;
&#x2F;* Включите экспериментальные функции веб-платформы *&#x2F;
&#x2F;* на странице настроек chrome:&#x2F;&#x2F;flags *&#x2F;

&#x2F;* «Котик» также работает и на нативных элементах *&#x2F;
video ^^ input[type=&quot;button&quot;] {
  background-color: red;
}</code></pre>
<p>See the Pen <a href='http://codepen.io/matmuchrapna/pen/Jibjz'>Стилизация нативных элементов с помощью селектора «Котик»</a> by Vladimir Starkov (<a href='http://codepen.io/matmuchrapna'>@matmuchrapna</a>) on <a href='http://codepen.io'>CodePen</a></p>
</div><script async src="//codepen.io/assets/embed/ei.js"></script>

[1]: http://robdodson.me/blog/2013/08/29/shadow-dom-styles-cont-dot#parts
[3]: https://www.google.com/intl/en/chrome/browser/canary.html
[4]: http://codepen.io/robdodson/pen/EhIax
[5]: http://codepen.io/robdodson
[6]: http://codepen.io
[7]: http://codepen.io/robdodson/pen/wFqJg
[8]: https://twitter.com/Volker_E/status/401202275009310722
[9]: http://codepen.io/robdodson/pen/iaJHd
