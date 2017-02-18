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

## CSS 实战技术

* 使用web字体

    ```
    所有主流浏览器都支持Web字体，使用Web字体时，浏览器会从Web服务器中下载字体，然后显示网页中的字体
    
    css中设定web字体的方式：
        1. @font-face指令，负责告诉浏览器字体的名称和下载地址
        2. font-family属性，指定web字体的方式与指定电脑中已安装字体的方式一样

    字体文件的类型
        1. EOT（嵌入式OpenType）,只有IE支持这种字体
        2. TrueType和OpenType，电脑中的.ttf .otf格式的字体，电脑字体最常使用这两种格式。这两种字体格式可以在文字处理软件和桌面出版软件里使用，也可以在网页中使用
        3. WOFF，Web开放字体格式时专为web设计的，基本上算是TrueType或OpenType格式的压缩版，因此文件体积通常较小，比其他字体格式下载得快
    ```
    * 为文本着色
    
        ```
        RGB
            红 绿 蓝
        RGBA    IE8以前的版本不兼容
            红 绿 蓝 透明度
        HSL
            eg: color: hsl(0. 100%, 50%);
            第一个参数是角度，取值范围是0-360,对应于色圆
            第二个参数是饱和度，即颜色的纯度
            第三个参数是亮度
        ```
    
    * 修改字号

        ```
        px 
        关键字
            xx-small x-small small
            medium large x-large xx-large
        百分比
            相对于父元素字体的大小
        em
            和百分比的原理相似
        rem
            字号的大小根据根元素来决定
        ```
        
        * 装饰词语和字符
        
            ```
            font-style
            font-weight
                100-900 
            text-transform
                uppercase 大写
                lowercase 小写
                capitalize 首字母变成大写
            text-decoration
                underline
                overline
                line-through
                blink
            text-shadow
                1. 横向偏移值
                2. 纵向偏移值
                3. 阴影的模糊程度
                4. 投影的颜色
            ```
        * 装饰整个段
        
            ```
            line-height
                使用%/em 可以使行间距会随着font-size属性的值按比例变化
                默认的line-height: 120%;
                使用数字设定行间距
                    line-height: 1.5;
                    遇到这种值时，浏览器会拿它乘以字号，确定行高是多少，然而由于嵌套的标签会从父辈标签继承line-height属性的值，如果使用em／%为单位设定行间距，会遇到问题，因为line-heighth会继承，而且继承的不是百分数，而是计算得到的具体行高
            
            text-align
            text-indent 首行缩进
            ```
            
        * 装饰列表el
        
            ```
            list-style-type
            list-style-position
            list-style-image
            ```
            
        * 外边距冲突

            ```
            解决办法：
                1. 设定一些内边距
                2. 添加边框，因为两个外边距之间有边框或内边距，因此不再相连。
            把外边距设为负值，去掉空白
            ```
            
        * 投影

            ```
            box-shadow
                第一个参数： 横向偏移
                第二个参数： 纵向偏移
                第三个参数： 投影的半径
                第四个参数： 投影的颜色
             投影会强制浏览器多次重新渲染和重新绘制，所以要慎重选择
            ```
        * 浮动对背景和边框的影响
            
            ```
            web浏览器只会让文字围绕浮动的元素显示，而不包括边框或者背景，解决办法
                1. 为浮动元素下面设置了背景或边框的元素添加一个样式规则，找到样式后，添加这一行代码:overflow: hidden
                2. 在浮动元素的四周添加边框线，如果边框线足够宽，而且颜色于页面的背景色一样，边框看起来就像是空白的
            ```     
        
        * clear 不要围着浮动的元素显示
            
            ```
            left 让元素显示在左浮动的元素下面，不过仍然围着右浮动的元素
            right 让元素显示在右浮动的元素下面，不过仍然围着左浮动的元素
            both 强制让元素显示在左浮动和右浮动的元素下面
            ```
* 背景图
    
    ```
    background-attachment
        scroll 背景图与文本和页面中的其他内容一起滚动
        fixed  把背景图固定在某个位置
    background-origin 重新定义图像的起点
        border-box: 从边框的左上角开始放置背景图
        padding-box: 从内边距的左上角开始放置背景图
        content-box: 从内容区域的左上角开始放置
    background-size
        contain 根据元素的背景尺寸强制调整图像的尺寸
        cover 强制让图像的宽度适应元素的宽度，让图像的高度适应元素的高度，而且不破坏图像的纵横比
    background-image: url(...) center top no-repeat,
                      url(...) center center no-repeat,
                      url(...) center bottom no-repeat
                      
    ```   
 * CSS 变形，过渡和动画
 
    ```
    transform 使用这个属性时要指定变形的类型以及表示变形程度的值
        rotate(deg) 顺时针旋转
        scale(n) 放大n倍 负数则翻转
        translate(x, y) 平移
        skew(deg, deg) 倾斜
        translateZ(0) 表示用GPU加载
    transform-origin 修改变形原点
    
    过渡满足的条件
        两个样式
        transition属性
            transition-property 指定要以动画方式变化的属性(所有属性则用all)
            transition-duration 指定动画持续时间长度
        触发器
            transition-tinming-function 动画的速率
                linear
                ease
                ease-in
                ease-out
                ease-in-out
            transition-delay 延迟动画的加载
            
    动画
        css过渡只能把一系列CSS属性葱一个状态变到另外一个状态，css动画则能把一系列CSS属性从一个状态变到另一个状态。再变到第三个状态还可以继续变化，还可以重播动画，暂停动画，倒播动画
        
        创建动画两步
            1. 定义动画， 设置关键帧，列出要变化的css属性
            2. 把动画应用到元素上
        
        @keyframse animationName {
            from {
                // ...
            }
            to {
                // ...
            }
        }
        
        .className {
            animation-name: animationName;
            animation-duration: time;
        }
         
         animation-timing-function  控制整个动画的播放速率
         animation-iteration-count 播放次数
         animation-direction 播放的方向
         animation-play-state running paused
    ``` 
    


