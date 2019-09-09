# Navigation
วิธีการทำ Navigation ในแอพแอนดรอยด์โดย Kotlin

เริ่มต้นจากการสร้างโปรเจ็คขึ้นมาก่อนโดยมีรายละเอียดตามรูปเลยครับ

<p align="center">
  <img src="https://tgf-programing.com/uploads/temp//1568050041-1vYFT.jpg">
</p>

ขั้นตอนที่สองก็ให้ทำการตั้งชื่อแอพพลิเคชั่น โดยในที่นี้ขอตั้งชื่อว่า NavigationDemo จะบันทึกไว้ตรงไหนก็แล้วแต่ความสะดวก
และในส่วนของ Language ให้เลือกเป็น Kotlin ส่วน API Level ให้เลือกเป็น API 19: Android 4.4 (Kitkat) หลักจากนั้น
กด Finish
<p align="center">
  <img src="https://tgf-programing.com/uploads/temp//1568050169-kHUal.jpg">
</p>

เมื่อเข้ามาหน้าเริ่มต้นก็จะพบกับหน้าจอแบบนี้

<p align="center">
  <img src="https://tgf-programing.com/uploads/temp//1568050309-4nxuM.jpg">
</p>

ก่อนอื่นเลยให้เราทำการเปิดไฟล์ Build.gradle ขึ้นมาแล้วทำการเพิ่ม dependencies ต่างเข้าไปดังนี้
```
implementation 'com.google.android.material:material:1.0.0'
```
ก็จะได้โครงสร้างหน้าตาไฟล์มาเป็นลักษณะดังภาพ

<p align="center">
  <img src="https://tgf-programing.com/uploads/temp//1568050542-Zs2Pp.jpg">
</p>

หลังจากนั้นให้กด Sync Now เมื่อกดเรียบร้อยแล้วให้เราไปที่ไฟล์ app > res > layout > activity_main.xml ให้เราทำการแก้ไขเนื้อหาไฟล์ให้เป็นดังนี้
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.drawerlayout.widget.DrawerLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/drawer_layout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:openDrawer="start">

    <include
        layout="@layout/app_bar_main"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

    <com.google.android.material.navigation.NavigationView
        android:id="@+id/nav_view"
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:layout_gravity="start"
        app:headerLayout="@layout/nav_header_main"
        app:menu="@menu/activity_main_drawer" />

</androidx.drawerlayout.widget.DrawerLayout>
```
จากนั้นทำการเพิ่มไฟล์ใหม่ โดยการคลิ๊กขวาที่โฟลเดอร์ layout > New > Layout resource rile ในช่อง File name  ให้ตั้งชื่อเป็น app_bar_main จากนั้นกด OK

<p align="center">
  <img src="https://tgf-programing.com/uploads/temp//1568050910-ztEaz.jpg">
</p>

เปิดไฟล์และแก้ไขเนื้อหาให้เป็นดังนี้
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.coordinatorlayout.widget.CoordinatorLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <com.google.android.material.appbar.AppBarLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:fitsSystemWindows="true"
        android:theme="@style/AppTheme.AppBarOverlay">

        <androidx.appcompat.widget.Toolbar
            android:id="@+id/toolbar_main"
            android:layout_width="match_parent"
            android:layout_height="?attr/actionBarSize"
            android:background="?attr/colorPrimary"
            app:layout_scrollFlags="scroll|enterAlways"
            app:popupTheme="@style/AppTheme.PopupOverlay" />

    </com.google.android.material.appbar.AppBarLayout>
</androidx.coordinatorlayout.widget.CoordinatorLayout>
```
และสร้างไฟล์ใหม่อีกครั้งโดยการกดคลิ๊กขวาที่โฟลเดอร์ layout > New > Layout resource rile ในช่อง File name  ให้ตั้งชื่อเป็น nav_header_main จากนั้นกด OK
<p align="center">
  <img src="https://tgf-programing.com/uploads/temp//1568051145-7eEWS.jpg">
</p>

และเปลี่ยนโค้ดเป็นดังนี้
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/nav_header"
    android:layout_width="match_parent"
    android:layout_height="160dp"
    android:background="@color/colorAccent"
    android:clickable="true"
    android:focusable="true"
    android:foreground="?attr/selectableItemBackgroundBorderless"
    android:gravity="bottom"
    android:orientation="vertical"
    android:padding="16dp"
    android:theme="@style/ThemeOverlay.AppCompat.Dark">

    <ImageView
        android:id="@+id/nav_header_imageView"
        android:layout_width="64dp"
        android:layout_height="64dp"
        android:src="@mipmap/ic_launcher" />

    <TextView
        android:id="@+id/nav_header_textView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:paddingTop="16dp"
        android:text="Chike Mgbemena"
        android:textAppearance="@style/TextAppearance.AppCompat.Body1" />
</LinearLayout>
```
ทำการสร้างโฟลเดอร์ใหม่ โดยการคลิ๊กขวาที่ res เลือก New > Android Resource Directory ช่อง Directory name ให้ใส่เป็นคำว่า menu แล้วกด Ok

<p align="center">
  <img src="https://tgf-programing.com/uploads/temp//1568051365-G68Vi.jpg">
</p>

ทำการสร้างไฟล์เมนูใหม่ โดยการ คลิ๊กขวาที่ โฟลเดอร์ menu ที่เราสร้างใหม่เมื่อสักครู่แล้วทำการเลือก New > Menu resource file และตั้งชื่อไฟล์ว่า activity_main_drawer
<p align="center">
  <img src="https://tgf-programing.com/uploads/temp//1568051481-FROfV.jpg">
</p>

แก้ไขโค้ดให้เป็นดังนี้
```
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <group>
        <item android:id="@+id/nav_item_one"
            android:title="Item 1" />
        <item android:id="@+id/nav_item_two"
            android:title="Item 2" />
        <item android:id="@+id/nav_item_three"
            android:title="Item 3" />
    </group>
    <group android:id="@+id/group_menu">
        <item android:id="@+id/nav_item_four"
            android:title="Item 4" />
        <item android:id="@+id/nav_item_five"
            android:title="Item 5" />
    </group>
    <item android:title="Title 1">
        <menu>
            <item android:id="@+id/nav_item_six"
                android:title="Item 6" />
            <item android:id="@+id/nav_item_seven"
                android:title="Item 7" />
        </menu>
    </item>
</menu>
```

มาถึงตรงนี้เรามากันไกลเกินกว่าครึ่งทางแล้วครับ ต่อไปก็จะเป็นในส่วนการตั้งค่าเพิ่มเติม โดยให้เราไปที่ app > res > values > strings.xml เพิ่มโค้ด 2 ตัวนี้เข้าไปครับ
```
  <string name="navigation_drawer_open">เปิด</string>
  <string name="navigation_drawer_close">ปิด</string>
```
ผลลัพธ์ที่ได้จะเป็นดังภาพ
<p align="center">
  <img src="https://tgf-programing.com/uploads/temp//1568051653-mMQJd.jpg">
</p>

และอีกไฟล์ app > res > values > styles.xml ให้แก้ไขไฟล์ใหม่โดยนำโค้ดชุดนี้เข้าไปแทน

```
<resources>
<style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">
    <item name="colorPrimary">@color/colorPrimary</item>
    <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
    <item name="colorAccent">@color/colorAccent</item>
    <item name="windowActionBar">true</item>
    <item name="windowNoTitle">true</item>
</style>
<style name="AppTheme.AppBarOverlay" parent="ThemeOverlay.AppCompat.Dark.ActionBar" />
<style name="AppTheme.PopupOverlay" parent="ThemeOverlay.AppCompat.Light" />
</resources>
```
<p align="center">
  <img src="https://tgf-programing.com/uploads/temp//1568051789-3Jscc.jpg">
</p>

และส่วนสุดท้ายแก้ไขไฟล์ MainActivity โดยแก้ไขไฟล์ให้เป็นดังนี้
```
import android.content.res.Configuration
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.MenuItem
import android.widget.Toast
import androidx.appcompat.app.ActionBarDrawerToggle
import androidx.appcompat.widget.Toolbar
import androidx.drawerlayout.widget.DrawerLayout
import com.google.android.material.navigation.NavigationView

class MainActivity : AppCompatActivity(), NavigationView.OnNavigationItemSelectedListener {

    private lateinit var drawer: DrawerLayout
    private lateinit var toggle: ActionBarDrawerToggle

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        val toolbar: Toolbar = findViewById(R.id.toolbar_main)
        setSupportActionBar(toolbar)
        drawer = findViewById(R.id.drawer_layout)
        toggle = ActionBarDrawerToggle(this, drawer, toolbar, R.string.navigation_drawer_open, R.string.navigation_drawer_close)
        drawer.addDrawerListener(toggle)
        supportActionBar?.setDisplayHomeAsUpEnabled(true)
        supportActionBar?.setHomeButtonEnabled(true)
        val navigationView: NavigationView = findViewById(R.id.nav_view)
        navigationView.setNavigationItemSelectedListener(this)
    }

    override fun onPostCreate(savedInstanceState: Bundle?) {
        super.onPostCreate(savedInstanceState)
        toggle.syncState()
    }

    override fun onConfigurationChanged(newConfig: Configuration?) {
        super.onConfigurationChanged(newConfig)
        toggle.onConfigurationChanged(newConfig)
    }

    override fun onOptionsItemSelected(item: MenuItem?): Boolean {
        if (toggle.onOptionsItemSelected(item)) {
            return true
        }
        return super.onOptionsItemSelected(item)
    }

    override fun onNavigationItemSelected(item: MenuItem): Boolean {

        when (item.itemId) {
            R.id.nav_item_one -> Toast.makeText(this, "Clicked item one", Toast.LENGTH_SHORT).show()
            R.id.nav_item_two -> Toast.makeText(this, "Clicked item two", Toast.LENGTH_SHORT).show()
            R.id.nav_item_three -> Toast.makeText(this, "Clicked item three", Toast.LENGTH_SHORT).show()
            R.id.nav_item_four -> Toast.makeText(this, "Clicked item four", Toast.LENGTH_SHORT).show()
        }
        return true
    }
}
```

สำหรับมือใหม่ให้ระวังด้วยไม่ต้องเอาไปทับบรรทัดแรกที่เป็น package นะครับ
จากนั้นลองกดรันดูก็จะได้แอพที่มีแถบเมนู navigation แล้วครับ
