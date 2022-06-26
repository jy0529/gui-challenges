0. Button Object
    property:
        type: submit | button | reset
    state
        disabled
    input buttons:
        type=button
        type=file
    css:
        hover
        active
        focus
        focus-visible

1. HTML Markup
<form>
    <button>default</button>
    <button type="submit">Submit</button>
    <button type="button">Type Button</button>
    <button type="reset">Reset</button>
    <button disabled">Disabled Button</button>
    <button class="button-custom">Custom</button>
    <input type="file"></input>
</form>

2. Accessibility
    Hover and focus together
    Interactive focus ring
    Ensuing passing color contrast
    Hiding icons from folks who can't see

3. Styles
    An adaptive custom property strategy
    Preparing for design consistency
    Styling buttons
    Creating variants


1. :is and :where?
    组合查询，更方便，:is you优先级，:where 优先级为 0

2. color contrast ?
    无障碍化，前景色与背景色的差异比，保证视力低下的人能看清

3. prefers-color-scheme ?
    选择亮色主题还是黑色主题

4. why hsl ? hex or rgb ?


5. why ch unit ?
    相对于 0 这个字的大小

6. ::file-selector-button ?
    文件选择器按钮 伪类

7. prefers-reduced-motion: no-preference ?
    动画功能没被减弱

8. why line-height: 1.5

9. touch-action: manipulation; ?
    能够减少浏览器判断是否双击等操作

10. why rem ?

11. why block-size and inline-size ?

12. margin-inline-end ?
