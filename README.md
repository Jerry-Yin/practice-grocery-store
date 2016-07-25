# -
实习期杂货铺

－－－－－2016.04.7－－－－－

1. 给 Android 开发者的 RxJava 详解：
    http://gank.io/post/560e15be2dca930e00da1083


2. 遇到的问题以及解决：

    问题一：
             由于 布局界面中  android:background="@drawable/background" 的引用，drawable图片资源较大，并且单纯的放置在 --drawable文件夹下面； 造成不同分辨率设备上内存急剧消耗，从而影响整个app的性能以及后续由于内存占用引起的一系列问题。

    解决方式：
            1.最好是在制作图片的时候制作不同分辨率的图片，并且分别放置在对应的不同分辨率的文件夹下面；如果只有一张图片并且比较大的话，就放置到高分辨率的文件夹中；
            2.手动释放内存，在onDestory()方法中 通过 如下方式回收： （或者直接用drawadlez对象，将其回调制空）
                 Drawable drawable = mBgdLayout.getBackground();
                 BitmapDrawable bd = (BitmapDrawable) drawable;
                 Bitmap bitmap = bd.getBitmap();
                 bitmap.recycle();
                 
    类似的内存泄漏 文章： 
                        http://blog.csdn.net/newcman/article/details/7675592
                        http://blog.sina.com.cn/s/blog_73e890f401016nmw.html

3. RecyclerView 的滑动卡顿问题，待解决...

4. RXJava 相关资料：
        http://wiki.jikexueyuan.com/project/rxjava/README.html

5. Rect Native
        http://wiki.jikexueyuan.com/project/react-native/
        http://reactivex.io./languages.html


－－－－－2016.07.13－－－－－

1. 后台长期运行的service实现：
        采用Service ＋ BroadcastReceiver 的组合方式实现； 开启服务后在 onStartCommand()方法中发送广播，广播接收到之后又会调用 startService() 或者 stopService()方法来开启或者结束服务，从而达到长期运行的效果。

2. 一个倒计时的动画效果，基于开源项目Arcprogress 做了稍微修改，效果上是 把之前绑定死的进度和文字进行了解绑，其实是在自定义view的代码中添加了一个TextView,来现实自己想要显示的东西，可以在外部提供显示的数据源以及显示方式。


－－－－－2016.07.25－－－－－
1. 关于多个view控件的效果叠加关系：
        问题需求描述：两个view控件（比如button）原本是各自独立的，但是我们现在的一个需求是在触发一个控件的时候另外一个控件也需要实现相应的变化效果；
        实现方案思路： 1.通过线程以及handler来完成；
                       2.给第一个控件添加一个OnTouchListener监听接口，在onTouch（）方法里来通过MoveEvent来设置另外一个控件的显示效果；


