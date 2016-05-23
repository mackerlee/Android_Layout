# Android_Layout

android 34-35 lesson:
1. linnerLayout:线性布局，按照水平(从左到右)或垂直(从上到下)方向布局组件，也是一个view，相当于容器可以把很多组件放进来;
2. res->layout->myactivity_main.xml:
    <?xml version="1.0" encoding="utf-8"?>
    //--LinearLayout是根元素布局，后面是一个命名空间，固定的写法，根元素必须有一个命名空间
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"  
        //--布局宽：match_parent匹配父组件，父组件多大她就多大，在这根组件匹配的是屏幕大小,fill_parent与match一样，现在都用match
        android:layout_width="match_parent"
        //--布局高：wrap_content是高度或宽度根据内容而定，内容有多少宽高就有多少,也可以用数字表示大小，如10dp，表示大小固定为10
        android:layout_height="match_parent"    
        android:orientation="vertical"> //垂直布局，horizontal是水平布局
    
        //--在布局中添加一个Textview组件
        <TextView
          android:id="@+id/TextView01"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"    //以上三个属性几乎每个组件都要有的,如果不取值id可以不用
          android:text="LinearLayout布局"         //显示的文本
          />
        <EditText
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="@string/to" />          //提示信息：显示在String.xml中定义名称为to的字符串内容
        <EditText
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="@string/subject" />
        <EditText
            android:layout_width="match_parent"
            android:layout_height="0dp"           //如果需要设置weight则高（水平布局则为宽)设为0，因为他已经不起作用了
            //--weight权重：比重的意思，在其中所占的比例,1表示在这个平级组件中所占的比重，其他都没有指定weight，则其他高匹配内容后则其他剩余的空间都给这个组件,如果有两个组件有weight则剩余的空间在这两个组件之间分配
            android:layout_weight="1"             
            android:gravity="top"                 //gravity:里面内容的位置,top表示从上面开始
            android:hint="@string/message" />
        <Button
            android:layout_width="100dp"
            android:layout_height="wrap_content"
            android:layout_gravity="right"        //layout_gravity：是指整个组件所在布局中的位置
            android:text="@string/send" />

    </LinearLayout>

3. res->values->string.xml:
    //--定义程序中需要用到的字符串
    <resources>
        <string name="app_name">Android_34</string>
        <string name="to">TO</string>
        <string name="subject">Subject</string>
        <string name="message">Message</string>
        <string name="send">Send</string>
    </resources>
4. 在启动android程序时如果希望调用自己写的myactivity_main.xml做为主activity，则需要在app->java->包名->MainActivity.java中:
    package com.example.mackerlee.android_34;

    import android.support.v7.app.AppCompatActivity;
    import android.os.Bundle;
    
    public class MainActivity extends AppCompatActivity {
    
        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.myactivity_main);  //设置为我们自定义的activity
        }
    }

android 36-38 lesson:
1.RelativeLayout相对布局：相对其它组件的布局方式,有依赖关系的，官方推荐的布局方式，linnerlayout可以嵌套而Relativelayout不可以                           嵌套.
2.创建一个相对布局res->layout->myactivity_main3.xml:
    <?xml version="1.0" encoding="utf-8"?>
    <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:paddingLeft="16dp"          //paddingLeft:布局里的内容距离左边内边距，如下面的EditText文本框内容距离左边框16dp
        android:paddingRight="16dp" >
        <EditText
            android:id="@+id/name"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="@string/reminder" />
        //--Spinner组件,相当于一个下拉列表
        <Spinner
            android:id="@+id/dates"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_below="@id/name"         //layout_below:表示该控件位于给定ID的控件下面
            android:layout_alignParentLeft="true"   //layout_alignParentLeft:该控件左边对齐父控件左边
            android:layout_toLeftOf="@+id/times" /> //layout_toLeftOf:该控件位于指定ID控件的左边，即下面spinner的左边
        <Spinner
            android:id="@id/times"
            android:layout_width="96dp"
            android:layout_height="wrap_content"
            android:layout_below="@id/name"
            android:layout_alignParentRight="true" />
        <Button
            android:layout_width="96dp"
            android:layout_height="wrap_content"
            android:layout_below="@id/times"
            android:layout_alignParentRight="true"
            android:text="@string/done" />
    </RelativeLayout>
3.如果用linnerlayout实现上述布局必须使用布局嵌套，所以用相对布局性能和效果都更好.

4.TableLayout:用表格的方式实现布局.
5.FrameLayout:帧布局，每个组件都是是从屏幕的左上角坐标开始布局,后一个子控件会层叠前一个子控件，无法给子控件指定位置.

android 39 lesson:
1.AbsoluteLayout绝对布局:根据绝对坐标来布局,指定了子元素准确的x/y值，该布局没有屏幕边框，允许元素之间相互重叠.
2.布局工具：在C:\Users\mackerlee\AppData\Local\Android\sdk\tools文件夹中的hierarchyviewer分层视图查看工具,该工具必须与模拟器关             联使用，当启动模拟器运行app后，点击hierarchyviewer中的刷新Refresh，则会显示该模拟器信息，比如加载的工程等等，Load             View Hierarchy是加载视图分层按钮，inspect Screenshot是用精确位置去调整查看布局方式.
            hierarchyviewer工具必须处于运行模式才能使用，调试模式是不能使用的
            
