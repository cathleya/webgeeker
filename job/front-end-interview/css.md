```html
<!-- 1.如何居中一个浮动元素 -->

<!-- 父元素和子元素同时左浮动，然后父元素相对左移动50%，再然后子元素相对右移动50%，或者子元素相对左移动-50%也就可以了。 -->


<style type="text/css">
    .p{
        position:relative;
        left:50%;
        float:left;
    }
    .c{
        position:relative;
        float:left;
        right:50%;
    }
</style>


<div class="p">

    <h1 class="c">Test Float Element Center</h1>

</div>



<!-- 2.css实现水平垂直居中 -->

<style type="text/css">
    .align-center{
        /**
         * 负边距+定位：水平垂直居中（Negative Margin）
         * 使用绝对定位将content的定点定位到body的中心，然后使用负margin（content宽高的一半），
         * 将content的中心拉回到body的中心，已到达水平垂直居中的效果。
         */
        position:absolute;
        left:50%;
        top:50%;
        width:400px;
        height:400px;
        margin-top:-200px;
        margin-left:-200px;
        border:1px dashed #333;
    }
</style>

<!-- 3.css实现三栏布局，中间自适应 -->



/*方法一：自身浮动法。左栏左浮动，右栏右浮动。*/

<style type='text/css'>
.left , .right{
            height: 300px;
            width: 200px;
        }
        .right{
            float: right;
            background-color: red;
        }
        .left{
            float: left;
            background-color: #080808;
        }
        .middle{
            height: 300px;
            margin: 0 200px;//没有这行，当宽度缩小到一定程度的时候，中间的内容可能换行
            background-color: blue;
        }
</style>




<!-- 方法二：margin负值法 -->

<style type="text/css">
            body{
                margin: 0;
                padding: 0;
            }
            .left , .right{
                height: 300px;
                width: 200px;
                float: left;
            }
            .right{
                margin-left: -200px;
                background-color: red;
            }
            .left{
                margin-left: -100%;
                background-color: #080808;
            }
            .middle{
                height: 300px;
                width: 100%;
                float: left;
                background-color: blue;
            }
</style>



    <!--放第一行-->

    <div class="middle">middle</div>

    <div class="left">left</div>

    <div class="right">right</div>





<!-- 方法三：绝对定位法。左右两栏采用绝对定位，分别固定于页面的左右两侧，中间的主体栏用左右margin值撑开距离。 -->



<style>
    body{
        margin: 0;
        padding: 0;
    }
    .left , .right{
        top: 0;
        height: 300px;
        width: 200px;
        position: absolute;
    }
    .right{
        right: 0;
        background-color: red;
    }
    .left{
        left: 0;
        background-color: #080808;
    }
    .middle{
        margin: 0 200px;
        height: 300px;
        background-color: blue;
    }
</style>


<div class="left">left</div>

<!--这种方法没有严格限定中间这栏放置何处-->

<div class="middle">middle</div>

<div class="right">right</div>

``` 

