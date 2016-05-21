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
4. 
