CircularReveal
==============

Lollipop ViewAnimationUtils.createCircularReveal for android api 14


How to use:
======

Use regular `RevealFrameLayout` & `RevealLinearLayout` don't worry, only target will be clipped :)

```xml
<io.codetail.widget.RevealFrameLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- Put more views here if you want, it's stock frame layout  -->

    <android.support.v7.widget.CardView
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:id="@+id/awesome_card"
        style="@style/CardView"
        app:cardBackgroundColor="@color/material_deep_teal_500"
        app:cardElevation="2dp"
        app:cardPreventCornerOverlap="false"
        app:cardUseCompatPadding="true"
        android:layout_marginLeft="8dp"
        android:layout_marginRight="8dp"
        android:layout_marginTop="8dp"
        android:layout_width="300dp"
        android:layout_height="300dp"
        android:layout_gravity="center_horizontal"
        />

</io.codetail.widget.RevealFrameLayout>
```

```java

    View myView = findView(R.id.awesome_card);

    // get the center for the clipping circle
    int cx = (myView.getLeft() + myView.getRight()) / 2;
    int cy = (myView.getTop() + myView.getBottom()) / 2;

    // get the final radius for the clipping circle
    int dx = Math.max(cx, myView.getWidth() - cx);
    int dy = Math.max(cy, myView.getHeight() - cy);
    float finalRadius = (float) Math.hypot(dx, dy);

    // Android native animator
    Animator animator =
            ViewAnimationUtils.createCircularReveal(myView, cx, cy, 0, finalRadius);
    animator.setInterpolator(new AccelerateDecelerateInterpolator());
    animator.setDuration(1500);
    animator.start();

```

How to add dependency
=====================


 add a library dependency

```groovy
 repositories {
        jcenter()


    }
	dependencies {
	    compile 'com.joe.animationtool:circualreveal:1.0.0'
	}
```



