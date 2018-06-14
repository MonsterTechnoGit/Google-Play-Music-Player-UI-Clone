# Google-Play-Music-Player-UI-Clone

[![](https://3.bp.blogspot.com/-9aXF7m5R7tQ/WyJuR3qpxKI/AAAAAAAAWJ0/-M6hAYuqiP0zmSsRTuuZv34ddkVAOWUBgCLcBGAs/s640/playMusic.jpg)](https://3.bp.blogspot.com/-9aXF7m5R7tQ/WyJuR3qpxKI/AAAAAAAAWJ0/-M6hAYuqiP0zmSsRTuuZv34ddkVAOWUBgCLcBGAs/s1600/playMusic.jpg)

 Hello guys in this post I will tell you how you can make **Google play music** like sliding up panel and also we design the Google play music player UI...


**1. Create new project.**
----------------------

* Create a new project in Android Studio from **File > New Project**and select **Basic Activity** from templates.or you can chose your existing project.

*  Add this dependency to your **app/build.gradle**. And **Sync** the project.
```java
{
    dataBinding {
        enabled = true
    }
}
 
dependencies {
    //...
 
    implementation 'com.sothree.slidinguppanel:library:3.4.0'
    implementation 'jp.wasabeef:blurry:2.1.1'
    implementation 'com.github.navasmdc:MaterialDesign:1.5@aar'
    
}
```
* Go to **app\\src\\main\\res\\values** and open **style.xml** file and change **Theme.AppCompat.Light.DarkActionbar** to **Theme.AppCompat.Light.NoActionBar**

* Now you need to add this **color code** to your project.
```xml
<resources>
    <color name="colorPrimary">#3F51B5</color>
    <color name="colorPrimaryDark">#a3391f</color>
    <color name="colorAccent">#F55730</color>
    <color name="backgroundColor">#ffff</color>
    <color name="tectColor">#000</color>
    <color name="songTimerColor">#484848</color>
</resources>
```
* Download the draweble images from here if you don't use them you can create your own.          
* Download: [**Drawable Images**](https://github.com/MonsterTechnoGit/Google-Play-Music-Player-UI-Clone/tree/master/app/src/main/res)
* Open **activity\_main.xml**file and past this code.
```xml
<?xml version="1.0" encoding="utf-8"?>
<com.sothree.slidinguppanel.SlidingUpPanelLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/activity_main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="bottom"
    tools:context=".MainActivity"
    app:umanoPanelHeight="70dp"
    app:umanoShadowHeight="5dp">

    <RelativeLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <TextView
            android:layout_centerInParent="true"
            android:textSize="26sp"
            android:text="Main Content"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" />
    </RelativeLayout>

    <RelativeLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent">


        <include layout="@layout/sample" />
    </RelativeLayout>

</com.sothree.slidinguppanel.SlidingUpPanelLayout>
```


* Now create a new activity under your Layout resource file and name it as **sample.xml** and past this code.
```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"

    >

    <ImageView
        android:src="@drawable/songs_cover"
        android:layout_centerInParent="true"
        android:layout_width="match_parent"
        android:scaleType="centerCrop"
        android:clickable="false"
        android:layout_height="match_parent" />

    <LinearLayout
        android:id="@+id/toolbar_layout"
        android:layout_width="match_parent"
        android:layout_height="70dp"
        android:orientation="horizontal"
        android:clickable="true"
        android:background="@color/backgroundColor"
        android:gravity="center">

        <android.support.constraint.ConstraintLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent">

            <ImageView
                android:id="@+id/songs_cover_one"
                android:layout_width="50dp"
                android:layout_height="50dp"
                android:layout_margin="10dp"
                android:layout_marginBottom="8dp"
                android:layout_marginTop="8dp"
                android:src="@drawable/songs_cover"
                app:layout_constraintBottom_toBottomOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintHorizontal_bias="0.0"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />

            <LinearLayout
                android:id="@+id/linearLayout"
                android:layout_width="202dp"
                android:layout_height="match_parent"
                android:layout_marginBottom="8dp"
                android:layout_marginEnd="8dp"
                android:layout_marginStart="8dp"
                android:layout_marginTop="8dp"
                android:orientation="vertical"
                app:layout_constraintBottom_toBottomOf="parent"
                app:layout_constraintEnd_toStartOf="@+id/linearLayout3"
                app:layout_constraintStart_toEndOf="@+id/songs_cover_one"
                app:layout_constraintTop_toTopOf="parent">

                <TextView
                    android:id="@+id/songs_title"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:fontFamily="sans-serif-condensed"
                    android:lines="1"
                    android:text="Havana (Camila Cabello song)"
                    android:textColor="@color/tectColor"
                    android:textSize="22dp" />

                <TextView
                    android:id="@+id/songs_artist_name"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:lines="1"
                    android:text="Camila Cabello" />

            </LinearLayout>

            <LinearLayout
                android:id="@+id/linearLayout3"
                android:layout_width="50dp"
                android:layout_height="50dp"
                android:layout_marginBottom="8dp"
                android:layout_marginEnd="8dp"
                android:layout_marginStart="8dp"
                android:layout_marginTop="8dp"
                android:gravity="center"
                app:layout_constraintBottom_toBottomOf="parent"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintHorizontal_bias="0.974"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent">

                <ImageButton
                    android:id="@+id/play_button"
                    android:layout_width="50dp"
                    android:scaleType="centerInside"
                    android:clickable="true"
                    android:focusable="true"
                    android:layout_height="50dp"
                    android:background="?attr/selectableItemBackgroundBorderless"
                    android:src="@drawable/round_play_arrow_black_48dp" />

                <ImageButton
                    android:id="@+id/pause_button"
                    android:layout_width="50dp"
                    android:scaleType="centerInside"
                    android:layout_height="50dp"
                    android:clickable="true"
                    android:focusable="true"
                    android:background="?attr/selectableItemBackgroundBorderless"
                    android:src="@drawable/round_pause_black_48dp"
                    android:visibility="gone" />
            </LinearLayout>

        </android.support.constraint.ConstraintLayout>

    </LinearLayout>

    <android.support.constraint.ConstraintLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true">

        <ImageButton
            android:layout_width="25dp"
            android:layout_height="25dp"
            android:layout_marginBottom="8dp"
            android:layout_marginEnd="8dp"
            android:layout_marginStart="8dp"
            android:layout_marginTop="8dp"
            android:scaleType="centerCrop"
            android:background="?attr/selectableItemBackgroundBorderless"
            android:src="@drawable/baseline_repeat_white_48dp"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.023"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            app:layout_constraintVertical_bias="0.811" />

        <ImageButton
            android:layout_width="25dp"
            android:layout_height="25dp"
            android:layout_marginBottom="8dp"
            android:layout_marginEnd="8dp"
            android:layout_marginStart="8dp"
            android:layout_marginTop="8dp"
            android:scaleType="centerCrop"
            android:background="?attr/selectableItemBackgroundBorderless"
            android:src="@drawable/baseline_shuffle_white_48dp"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.976"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            app:layout_constraintVertical_bias="0.811" />
    </android.support.constraint.ConstraintLayout>

    <android.support.constraint.ConstraintLayout
        android:layout_width="match_parent"
        android:layout_height="99dp"
        android:layout_alignParentBottom="true">


        <RelativeLayout
            android:id="@+id/relativeLayout"
            android:layout_width="match_parent"
            android:layout_height="80dp"
            android:clickable="false"
            android:background="@color/backgroundColor"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.0"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            app:layout_constraintVertical_bias="1.0">

            <android.support.constraint.ConstraintLayout
                android:layout_width="match_parent"
                android:layout_height="match_parent">

                <ImageButton
                    android:id="@+id/imageButton2"
                    android:layout_width="55dp"
                    android:layout_height="55dp"
                    android:padding="15dp"
                    android:layout_marginBottom="8dp"
                    android:layout_marginEnd="8dp"
                    android:layout_marginStart="16dp"
                    android:clickable="true"
                    android:focusable="true"
                    android:background="?attr/selectableItemBackgroundBorderless"
                    android:scaleType="centerCrop"
                    android:src="@mipmap/outline_thumb_up_alt_black_48"
                    app:layout_constraintBottom_toBottomOf="parent"
                    app:layout_constraintEnd_toEndOf="parent"
                    app:layout_constraintHorizontal_bias="0.0"
                    app:layout_constraintStart_toStartOf="parent"
                    app:layout_constraintTop_toBottomOf="@+id/StartTime"
                    app:layout_constraintVertical_bias="0.56" />
                <ImageButton
                    android:id="@+id/imageButton2new"
                    android:layout_width="55dp"
                    android:layout_height="55dp"
                    android:padding="15dp"
                    android:layout_marginBottom="8dp"
                    android:layout_marginEnd="8dp"
                    android:layout_marginStart="16dp"
                    android:visibility="gone"
                    android:clickable="true"
                    android:focusable="true"
                    android:scaleType="centerCrop"
                    android:background="?attr/selectableItemBackgroundBorderless"
                    android:src="@mipmap/baseline_thumb_up_alt_black_48"
                    app:layout_constraintBottom_toBottomOf="parent"
                    app:layout_constraintEnd_toEndOf="parent"
                    app:layout_constraintHorizontal_bias="0.0"
                    app:layout_constraintStart_toStartOf="parent"
                    app:layout_constraintTop_toBottomOf="@+id/StartTime"
                    app:layout_constraintVertical_bias="0.56" />
                <ImageButton
                    android:id="@+id/button"
                    android:layout_width="55dp"
                    android:layout_height="55dp"
                    android:padding="15dp"
                    android:layout_marginBottom="8dp"
                    android:layout_marginEnd="16dp"
                    android:layout_marginStart="8dp"
                    android:scaleType="centerCrop"
                    android:clickable="true"
                    android:focusable="true"
                    android:background="?attr/selectableItemBackgroundBorderless"
                    android:src="@mipmap/outline_thumb_down_alt_black_48"
                    app:layout_constraintBottom_toBottomOf="parent"
                    app:layout_constraintEnd_toEndOf="parent"
                    app:layout_constraintHorizontal_bias="1.0"
                    app:layout_constraintStart_toStartOf="parent"
                    app:layout_constraintTop_toBottomOf="@+id/endTime"
                    app:layout_constraintVertical_bias="0.56" />
                <ImageButton
                    android:id="@+id/buttontwo"
                    android:layout_width="55dp"
                    android:layout_height="55dp"
                    android:padding="15dp"
                    android:layout_marginBottom="8dp"
                    android:layout_marginEnd="16dp"
                    android:layout_marginStart="8dp"
                    android:visibility="gone"
                    android:scaleType="centerCrop"
                    android:clickable="true"
                    android:focusable="true"
                    android:background="?attr/selectableItemBackgroundBorderless"
                    android:src="@mipmap/baseline_thumb_down_alt_black_48"
                    app:layout_constraintBottom_toBottomOf="parent"
                    app:layout_constraintEnd_toEndOf="parent"
                    app:layout_constraintHorizontal_bias="1.0"
                    app:layout_constraintStart_toStartOf="parent"
                    app:layout_constraintTop_toBottomOf="@+id/endTime"
                    app:layout_constraintVertical_bias="0.56" />
                <TextView
                    android:id="@+id/StartTime"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_marginBottom="8dp"
                    android:layout_marginEnd="8dp"
                    android:layout_marginStart="8dp"
                    android:layout_marginTop="8dp"
                    android:fontFamily="sans-serif"
                    android:text="1:05"
                    android:textColor="@color/songTimerColor"
                    android:textSize="12sp"
                    app:layout_constraintBottom_toBottomOf="parent"
                    app:layout_constraintEnd_toEndOf="parent"
                    app:layout_constraintHorizontal_bias="0.0"
                    app:layout_constraintStart_toStartOf="parent"
                    app:layout_constraintTop_toTopOf="parent"
                    app:layout_constraintVertical_bias="0.0" />

                <TextView
                    android:id="@+id/endTime"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_marginBottom="8dp"
                    android:layout_marginEnd="8dp"
                    android:layout_marginStart="8dp"
                    android:layout_marginTop="8dp"
                    android:fontFamily="sans-serif"
                    android:text="3:06"
                    android:textColor="@color/songTimerColor"
                    android:textSize="12sp"
                    app:layout_constraintBottom_toBottomOf="parent"
                    app:layout_constraintEnd_toEndOf="parent"
                    app:layout_constraintHorizontal_bias="1.0"
                    app:layout_constraintStart_toStartOf="parent"
                    app:layout_constraintTop_toTopOf="parent"
                    app:layout_constraintVertical_bias="0.0" />

                <LinearLayout
                    android:id="@+id/linearLayout5"
                    android:layout_width="55dp"
                    android:layout_height="55dp"
                    android:layout_marginBottom="8dp"
                    android:layout_marginEnd="8dp"
                    android:layout_marginStart="8dp"
                    android:layout_marginTop="8dp"
                    android:gravity="center"
                    app:layout_constraintBottom_toBottomOf="parent"
                    app:layout_constraintEnd_toEndOf="parent"
                    app:layout_constraintHorizontal_bias="0.501"
                    app:layout_constraintStart_toStartOf="parent"
                    app:layout_constraintTop_toTopOf="parent"
                    app:layout_constraintVertical_bias="1.0">

                    <ImageButton
                        android:id="@+id/play_button_main"
                        android:layout_width="55dp"
                        android:layout_height="55dp"
                        android:scaleType="centerCrop"
                        android:clickable="true"
                        android:focusable="true"
                        android:background="?attr/selectableItemBackgroundBorderless"
                        android:src="@drawable/play_button" />
                    <ImageButton
                        android:id="@+id/pause_button_main"
                        android:layout_width="55dp"
                        android:visibility="gone"
                        android:scaleType="centerCrop"
                        android:layout_height="55dp"
                        android:clickable="true"
                        android:focusable="true"
                        android:background="?attr/selectableItemBackgroundBorderless"
                        android:src="@drawable/pause_button" />
                </LinearLayout>

                <ImageButton
                    android:layout_width="55dp"
                    android:layout_height="55dp"
                    android:layout_marginBottom="8dp"
                    android:layout_marginEnd="8dp"
                    android:layout_marginStart="8dp"
                    android:layout_marginTop="8dp"
                    android:background="?attr/selectableItemBackgroundBorderless"
                    android:padding="15dp"
                    android:clickable="true"
                    android:focusable="true"
                    android:scaleType="fitCenter"
                    android:src="@drawable/backword_button"
                    app:layout_constraintBottom_toBottomOf="parent"
                    app:layout_constraintEnd_toStartOf="@+id/linearLayout5"
                    app:layout_constraintHorizontal_bias="0.754"
                    app:layout_constraintStart_toEndOf="@+id/imageButton2"
                    app:layout_constraintTop_toTopOf="parent"
                    app:layout_constraintVertical_bias="1.0" />

                <ImageButton
                    android:id="@+id/imageButton"
                    android:layout_width="55dp"
                    android:layout_height="55dp"
                    android:layout_marginBottom="8dp"
                    android:layout_marginEnd="8dp"
                    android:layout_marginStart="8dp"
                    android:layout_marginTop="8dp"
                    android:clickable="true"
                    android:focusable="true"
                    android:background="?attr/selectableItemBackgroundBorderless"
                    android:padding="15dp"
                    android:scaleType="fitCenter"
                    android:src="@drawable/forword_button"
                    app:layout_constraintBottom_toBottomOf="parent"
                    app:layout_constraintEnd_toStartOf="@+id/button"
                    app:layout_constraintHorizontal_bias="0.25"
                    app:layout_constraintStart_toEndOf="@+id/linearLayout5"
                    app:layout_constraintTop_toTopOf="parent"
                    app:layout_constraintVertical_bias="1.0"
                     />
            </android.support.constraint.ConstraintLayout>
        </RelativeLayout>

        <SeekBar
            android:id="@+id/seekBar3"
            android:layout_width="0dp"
            android:layout_height="24dp"
            android:layout_marginBottom="8dp"
            app:layout_constraintBottom_toTopOf="@+id/relativeLayout"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.0"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="@+id/relativeLayout"
            app:layout_constraintVertical_bias="0.75" />
    </android.support.constraint.ConstraintLayout>
</RelativeLayout>
```
* Now this is the time to do some coding this is just to run the full UI you can code by yourself as you want. So open your **MainActivity.java** file and past this code.
```java
like = (ImageButton) findViewById(R.id.imageButton2);
        notlike = (ImageButton) findViewById(R.id.imageButton2new);
        dislike = (ImageButton) findViewById(R.id.button);
        notdislike = (ImageButton) findViewById(R.id.buttontwo);
        play = (ImageButton) findViewById(R.id.play_button);
        pause = (ImageButton) findViewById(R.id.pause_button);
        play_main = (ImageButton) findViewById(R.id.play_button_main);
        pause_main = (ImageButton) findViewById(R.id.pause_button_main);


        mLayout = (SlidingUpPanelLayout) findViewById(R.id.activity_main);

        like.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                notlike.setVisibility(View.VISIBLE);
                Toast.makeText(MainActivity.this,"You Like the Song",Toast.LENGTH_SHORT).show();
                if (notdislike.getVisibility() == View.VISIBLE){
                    notdislike.setVisibility(View.GONE);
                }
            }
        });

       notlike.setOnClickListener(new View.OnClickListener() {
           @Override
           public void onClick(View view) {
               notlike.setVisibility(View.GONE);
           }
       });

        dislike.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                notdislike.setVisibility(View.VISIBLE);
                Toast.makeText(MainActivity.this,"You DisLike the Song",Toast.LENGTH_SHORT).show();
                if (notlike.getVisibility() == View.VISIBLE){
                    notlike.setVisibility(View.GONE);
                }
            }
        });

        notdislike.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                notdislike.setVisibility(View.GONE);
            }
        });

        play.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                play.setVisibility(View.GONE);
                pause.setVisibility(View.VISIBLE);
                Toast.makeText(MainActivity.this,"Song Is now Playing",Toast.LENGTH_SHORT).show();
                if (play_main.getVisibility() == View.VISIBLE){
                    play_main.setVisibility(View.GONE);
                    pause_main.setVisibility(View.VISIBLE);
                }

            }
        });

        pause.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                pause.setVisibility(View.GONE);
                play.setVisibility(View.VISIBLE);
                Toast.makeText(MainActivity.this,"Song is Pause",Toast.LENGTH_SHORT).show();
                if (pause_main.getVisibility() == View.VISIBLE){
                    pause_main.setVisibility(View.GONE);
                    play_main.setVisibility(View.VISIBLE);
                }
            }
        });

        play_main.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                play_main.setVisibility(View.GONE);
                pause_main.setVisibility(View.VISIBLE);
                Toast.makeText(MainActivity.this,"Song Is now Playing",Toast.LENGTH_SHORT).show();
                if (play.getVisibility() == View.VISIBLE){
                    play.setVisibility(View.GONE);
                    pause.setVisibility(View.VISIBLE);
                }
            }
        });

        pause_main.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                pause_main.setVisibility(View.GONE);
                play_main.setVisibility(View.VISIBLE);
                Toast.makeText(MainActivity.this,"Song is Pause",Toast.LENGTH_SHORT).show();
                if (pause.getVisibility() == View.VISIBLE){
                    pause.setVisibility(View.GONE);
                    play.setVisibility(View.VISIBLE);
                }
            }
        });
    }

    @Override
    public void onBackPressed() {
        if (mLayout != null &&
                (mLayout.getPanelState() == PanelState.EXPANDED || mLayout.getPanelState() == PanelState.ANCHORED)) {
            mLayout.setPanelState(PanelState.COLLAPSED);
        } else {
            super.onBackPressed();
        }
    }
}
```
That's it now you can run your app and see how its look like thanks for your time. Hope you like this post. If you got any problem you can ask me in the comment section I will help you...
 Download the full source code from here-\> [Source code download](https://github.com/MonsterTechnoGit/Google-Play-Music-Player-UI-Clone)
