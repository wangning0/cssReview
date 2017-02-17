# CSS Review
* web字体的基本思想：链接字体文件，让网页可以使用任何字体，即使网站访客的电脑中没有安装你使用的字体也无妨
* 伪元素和伪类

    ```
    为了区别伪元素和伪类，伪元素可以使用双冒号表示，伪类单冒号表示，但是IE8以前不兼容双冒号的写法
    
    伪类：
        :focus
        :link
        :visited
        :hover
        :active
        :first-child
        :last-child
        :only-child
        :nth-child()
        :target
        :not()
    伪元素：
        first-line
        first-letter
        before
        after
        ::selection 鼠标按下后拖动的选择 css3(只能设置color和background-color)
    ```
* + 表示紧邻的兄弟元素， ～ 表示所有的兄弟元素
* 继承

    ```
    继承是指，应用在某个标签上的css属性传给了内部嵌套的标签，css属性也能隔代继承

    不能继承的属性：
        display、margin、border、padding、background、height、min-height、max- height、width、min-width、max-width、overflow、position、left、right、top、 bottom、z-index、float、clear、table-layout、vertical-align、page-break-after、 page-bread-before和unicode-bidi
    能继承的属性：
        所有元素可继承：visibility和cursor。
        内联元素可继承：letter-spacing、word-spacing、white-space、line-height、color、font、 font-family、font-size、font-style、font-variant、font-weight、text- decoration、text-transform、direction。
        块状元素可继承：text-indent和text-align。
        列表元素可继承：list-style、list-style-type、list-style-position、list-style-image。
        表格元素可继承：border-collapse。
    ```

* 层叠

    ```
    层叠是用于管控样式之间相互作用的方式，出现冲突时判断哪个样式的优先级高
    
    层叠规则：
        最近的祖辈胜出
        直接应用在标签上的样式胜出
        特指度
            一个标签选择符记 1分
            一个类选择符记 10分
            一个ID选择符记 100分
            一个行内样式记 1000分
    ```


