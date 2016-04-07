# -
实习期杂货铺


1. 给 Android 开发者的 RxJava 详解：
    http://gank.io/post/560e15be2dca930e00da1083


2. 遇到的问题以及解决：（2016.4.7）

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
4. 

