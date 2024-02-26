# Робота із анімацією та макетами в ОС Android

**Тема роботи:** Робота із анімацією та макетами в ОС Android.

**Мета роботи:** Отримати досвід роботи із анімацією та ознайомитись із
основними макетами для побудови користувацького інтерфейсу додатків під
ОС Android.

**Завдання 1 «Робота із анімацією»**

Створення в каталозі res каталогу anim, а в ньому файл з ship_anim.xml, що описує анімацію.
```xml
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <rotate
        android:duration="3333"
        android:fromDegrees="0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:repeatCount="infinite"
        android:repeatMode="reverse"
        android:toDegrees="1080" />
    <translate
        android:duration="1900"
        android:fromXDelta="-50%p"
        android:repeatCount="infinite"
        android:repeatMode="reverse"
        android:toXDelta="50%p" />
    <translate
        android:duration="1300"
        android:fromYDelta="-50%p"
        android:repeatCount="infinite"
        android:repeatMode="reverse"
        android:startOffset="123"
        android:toYDelta="50%p" />
    <alpha
        android:duration="500"
        android:fromAlpha="1.0"
        android:repeatCount="infinite"
        android:repeatMode="reverse"
        android:toAlpha="0.3" />
    <scale
        android:duration="10000"
        android:fromXScale="0.0"
        android:fromYScale="0.0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:repeatCount="infinite"
        android:repeatMode="reverse"
        android:toXScale="2.5" android:toYScale="2.5" />
</set>


```

У файлі розмітки activity_main.xml замінити елемент TextView на ImageView

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/shipView"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:src="@drawable/lander_plain"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

Додати рядки в кінці методу onCreate
```java
package com.example.animsample_anureva;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.ImageView;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        ImageView ship = (ImageView) findViewById(R.id.shipView);
        Animation shipAnim = AnimationUtils.loadAnimation(this, R.anim.ship_anim);
        ship.startAnimation(shipAnim);
    }
}

```
**Результат виконання програми**:

https://github.com/katushhiaa/PR_5/assets/113555695/f2ed3faf-eb72-47d7-a81e-f29f10b4e6b2


**Завдання 2 «Використання LinearLayout»** 
Локалізація додатку Hello Android World для французької мови.

Створити в каталозі res в каталозі values файл values-fr
```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="hello">Bonjour le monde Android</string>
    <string name="app_name">Keterina-fr</string>
    <color name="text_color">#fff</color>
    <color name="screen_bkg_color">#000</color>
    <color name="background">#000</color>
    <string name="button_text">Appuyez sur moi</string>

</resources>

```
Створити в каталозі layout файл activity_main.xml для французької мови

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text='@string/hello'
        android:background="@color/background"
        android:textColor="@color/text_color"
         />


    <LinearLayout
        android:layout_width="500dp"
        android:layout_height="381dp"
        android:layout_gravity="center"
        android:orientation="horizontal">

        <View
            android:layout_width="457dp"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:background="#0055A4" />

        <View
            android:layout_width="455dp"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:background="#FFFFFF" />

        <View
            android:layout_width="455dp"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:background="#EF4135" />
    </LinearLayout>


    <Button
        android:id="@+id/button2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="@color/but_name"
        android:text='@string/button_text' />

</LinearLayout>

```

Результат виконання програми:

![image](https://github.com/katushhiaa/PR_5/assets/113555695/2c4e39a1-6d79-4db9-bc31-1ef5e585e08b)

**Завдання 3 «Використання RelativeLayout»**
Додати потрібні рядки в файл strings.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="label_text">Введіть текст:</string>
    <string name="entry_hint">Поле введення</string>
    <string name="app_name">RelativeLayoutSample</string>
</resources>

```
Відредагувати файл activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android" android:layout_width="fill_parent"
    android:layout_height="fill_parent" >
    <TextView
        android:id="@+id/label"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:text="@string/label_text" />

    <EditText
        android:id="@+id/entry"
        android:layout_width="fill_parent"
        android:layout_height="50dp"
        android:layout_below="@id/label"
        android:background="@android:drawable/editbox_background"
        android:hint="@string/entry_hint" />
    <Button
        android:id="@+id/ok"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentRight="true"
        android:layout_below="@id/entry"
        android:layout_marginLeft="10dip"
        android:text="@android:string/ok" />

    <Button	android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignTop="@id/ok"
        android:layout_toLeftOf="@id/ok"
        android:text="@android:string/cancel" />
</RelativeLayout>

```

Запустити додаток

![image](https://github.com/katushhiaa/PR_5/assets/113555695/379dce1a-ed5b-47ea-ac39-1ec7707f4416)

Змінити тему в AndroidManifest.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.AppCompat.Light.DarkActionBar"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

Запустити додаток з новою темою

![image](https://github.com/katushhiaa/PR_5/assets/113555695/f52ea6a3-500f-4073-aa03-41b7ae8ed98b)
