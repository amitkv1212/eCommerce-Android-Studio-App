# GET PARTWISE README.md FILES[ HERE](https://github.com/amitkv1212/eCommerce-Android-Studio-App/tree/main/partwise%20-%20readmes "partwise readmes")

# Part 1 : [Creating Splash Screen for our App and starting with our Project](https://youtu.be/y6O7-H2OVXY "Part1")

**Create New Project**
***

Step 1:Create `Empty Activity` and Name as ->`SplashActivity.java`
***

Step 2:Go to `activity_splash.xml`and change the `constraint Layout` to  ~~constraint Layout~~ `Relative Layout`
***
Step 3 : Define an **ImageView** inside of `Realtive Layout`(so as to add icon)
>code as follows :
```

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#ffffff"
    tools:context=".SplashActivity">

    <ImageView
        android:layout_width="120dp"
        android:layout_height="120dp"
        android:src="@drawable/carts"
        android:layout_centerInParent="true"/>

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="eCommerce App All rights reserved "
        android:layout_centerInParent="true"
        android:layout_alignParentBottom="true"
        android:textColor="#626262"
        android:padding="20dp"/>

</RelativeLayout>
```
***

Step 4:Come to `SplashActivity.java` and we will use `Handler Method` for setting the time of the `Splash Screen`

***Go to `OnCreate Method` and declare as follows***:

>new Handler().postDelayed(new Runnable() {
>@Override
>            public void run() {
>                Intent i = new Intent(SplashActivity.this, MainActivity.class);
>                startActivity(i);
>                finish();
>            }
>        },3000);

**Note**: _3000 is the time in miliseconds which corresponds to 3 sec_

***

Step 5: Coming to `AndroidManifest.xml`

    and change the `Splashctivity` to `Launcher Activity` and `MainActivity` TO `DEFAULT` as follows by changing the Intent Filter as follows
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.aips.amit.amite_commerceapp">

    <application
        android:allowBackup="true"
        android:icon="@drawable/carts"
        android:label="@string/app_name"
        android:roundIcon="@drawable/carts"
        android:supportsRtl="true"
        android:theme="@style/Theme.AmitECommerceApp">
        <activity android:name=".SplashActivity"
            android:theme="@style/Theme.AppCompat.NoActionBar">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

‎‎‎  ‎ ‎‎   ‎ ‎  ‎‎‎‎‎‎‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎ ***-------------------------- <ins>PART  1</ins> --------------------------***


***
***
***

# Part 2 : [Designing our Login and Register Fragments](https://youtu.be/8vcWpJNnz40 "Part 2")

|<ins>Login Fragment |<ins>Register Fragment|
|---|---|
|![Image Source](https://github.com/amitkv1212/eCommerce-Android-Studio-App/blob/main/ScreenShots/Login%20Fragement.jpg?raw=true=10*10 "SignInFragment")|![ImageSource](https://github.com/amitkv1212/eCommerce-Android-Studio-App/blob/main/ScreenShots/Register%20Fragment.jpg?raw=true "SignUpFragement")   |


Note here : **`You can copy the Atrributes like width or height , copying the whole code may result into error as the id's defined in this project may vary in your case unless you define the same id's in your case`**



So in the first step we have created a Splash Screen and in this lets design our Activities

Step 1 : Go to the folder where `MainActivity.java ` exists and Create two new Fragments 1.)`Sign In Fragments` & 2.)`Sign Up Fragments`



Now lets design first `SignInFragments` so go to its `.xml ` file and code

- ~~constraintLayout~~ **Frame Layout** am=nd give background color as per your need by defining the attribute
>android:background="#colorcode"

- Now declare `constraintLayout` inside of `FrameLayout` for easier Designing

So inside `constraintLayout` first we will give an `imagebutton` as you can see in the design above picture


## Declare an Close image button for our app icon
***Common for both SignInFragment and SignUpFragement***
```
<ImageButton
            android:id="@+id/sign_in_close_btn"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:background="@android:color/transparent"
            android:padding="16dp"
            android:src="@drawable/ic_baseline_clear_24"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="1.0"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent" />
```
## Declare an ImageView for our app icon
***Common for both SignInFragment and SignUpFragement***

Code as follows:
```
<ImageView
            android:id="@+id/imageView"
            android:layout_width="120dp"
            android:layout_height="120dp"
            android:layout_marginTop="4dp"
            android:src="@drawable/carts"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/sign_in_close_btn" />
```

Now define two Editext as we are using email and password field where the user will enter the values

##   ‎ ‎‎‎  ‎ ‎‎   ‎ ‎  ‎ ‎‎‎  ‎ ‎‎   <ins> _*‎SignInFragment Designing Part*_</ins>

**Editext for Email id**:
```
<EditText
            android:id="@+id/sign_in_email"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginStart="20dp"
            android:layout_marginTop="20dp"
            android:layout_marginEnd="20dp"
            android:backgroundTint="#902E2929"
            android:ems="10"
            android:hint="Enter Your Email.."
            android:inputType="textEmailAddress"
            android:padding="16dp"
            android:textColor="@color/white"
            android:textColorHint="#902E2929"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.0"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/imageView" />
```

& **EditText for Password:**
```
<EditText
            android:id="@+id/sign_in_password"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginStart="16dp"
            android:layout_marginTop="10dp"
            android:layout_marginEnd="16dp"
            android:backgroundTint="#902e2929"
            android:ems="10"
            android:hint="Enter Password.."
            android:inputType="textPassword"
            android:padding="16dp"
            android:textColor="@color/white"
            android:textColorHint="#902e2929"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/sign_in_email" />
```

**Creating a Forget Password TextView**
```
<TextView
            android:id="@+id/sign_in_forget_password"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginStart="16dp"
            android:layout_marginTop="8dp"
            android:text="forgot password?"
            android:textColor="@color/white"
            app:layout_constraintStart_toStartOf="@+id/sign_in_password"
            app:layout_constraintTop_toBottomOf="@+id/sign_in_password" />
```

now **Define a sign in button :**

```
<Button
            android:id="@+id/sign_in_btn"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginStart="30dp"
            android:layout_marginTop="80dp"
            android:layout_marginEnd="30dp"
            android:background="@color/CCCC00"
            android:text="Sign in"
            android:textAllCaps="false"
            android:textSize="16sp"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.0"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/sign_in_password" />
```

***Create a `divider` and a text View `Or`***

Create `DontHave an account ` TextView
```
<TextView
            android:id="@+id/tv_dont_have_an_account"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Dont have an account?Sign up!"
            app:layout_constraintBottom_toBottomOf="parent"
            android:textColor="@color/white"
            android:textSize="18sp"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/textView2" />
```

## ‎‎‎‎‎‎‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎ <ins >_*SignUpFragement Designing*_</ins>

**EditText for Email id**

```
<EditText
            android:id="@+id/sign_up_email"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginStart="20dp"
            android:layout_marginTop="20dp"
            android:layout_marginEnd="20dp"
            android:backgroundTint="#902E2929"
            android:ems="10"
            android:hint="Enter Your Email.."
            android:inputType="textEmailAddress"
            android:padding="16dp"
            android:textColor="@color/white"
            android:textColorHint="#902E2929"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.0"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/imageView_sign_up" />
```

**EditText for Full Name**
```
<EditText
            android:id="@+id/sign_up_full_name"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginTop="12dp"
            android:ems="10"
            android:layout_marginStart="20dp"
            android:layout_marginEnd="20dp"
            android:inputType="textPersonName"
            android:hint="Full Name.."
            android:textColor="@color/white"
            android:padding="16dp"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.502"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/sign_up_email" />
```

**EditText for password**
```
<EditText
            android:id="@+id/sign_up_password"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginStart="16dp"
            android:layout_marginTop="68dp"
            android:layout_marginEnd="16dp"
            android:backgroundTint="#902e2929"
            android:ems="10"
            android:hint="Enter Password.."
            android:inputType="textPassword"
            android:padding="16dp"
            android:textColor="@color/white"
            android:textColorHint="#902e2929"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.0"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/sign_up_email" />
```

**Editext for Confirm Password**
```
<EditText
            android:id="@+id/sign_up_cnf_password"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginStart="20dp"
            android:layout_marginTop="12dp"
            android:layout_marginEnd="20dp"
            android:ems="10"
            android:hint="Confirm Password.."
            android:inputType="textPassword"
            android:padding="16dp"
            android:textColor="@color/white"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.502"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/sign_up_password" />
```

**Button for Sign Up**
```
<Button
            android:id="@+id/sign_up_btn"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_marginStart="30dp"
            android:layout_marginTop="80dp"
            android:layout_marginEnd="30dp"
            android:background="@color/CCCC00"
            android:text="Sign Up"
            android:textAllCaps="false"
            android:textSize="16sp"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.0"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/sign_up_password" />
```

**Already Have an Account TextView**
```
<TextView
            android:id="@+id/tv_already_have_an_account"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Already have an account?Sign in!"
            android:textColor="@color/white"
            android:textSize="18sp"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/textView92" />
```

 ‎‎‎‎‎‎‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎  ‎‎‎‎‎‎‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎  ‎‎‎‎‎‎‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎ ***-------------------<ins>PART - II</ins> ------------------***  ‎‎‎‎‎‎‎  ‎ ‎‎‎  ‎ ‎‎

 ***
 ***
***


  # [PART 3](https://youtu.be/huLq_0DJdoA "part 3")
  - Now after degigning Fragments we will come back to `activity main.xml` and put
 `Frame layout` inside of `Constraint layout`with attributes as follows:

 ```
 <FrameLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:layout_editor_absoluteX="194dp"
        android:id="@+id/register_frame_layout"
        tools:layout_editor_absoluteY="306dp">
 ```
***
 - Now coming to `MainActivity.java` :
 define `FrameLayout `variable there :
 >private FrameLayout framelayout;
 ***

 - Now in the `Oncreate` Mthod , find the `FrameLayout` ID as:
 >framelayout = findViewbyId(R.id.register_frame_layout);

 ***

 - Now set Fragments which we created i.e. `SignInFragment` and `SignUpFragment` into MainActivity by :
 `setFragment();` method

 Create this method :
 and code and start`Fragment Transaction `as follows:
 ```
 private void setFragemnt(Fragment fragemnt) {
        FragmentTransaction fragmentTransaction = getSupportFragmentManager().beginTransaction();
        fragmentTransaction.replace(frameLayout.getId(), fragemnt);
        fragmentTransaction.commit();
    }
 ```
***

 - **Pass the `SignInFragment ` at first because we want people to go to` sign in` screen at first then if he/she don't have an account then they can redirected by clicking `  dont have an account ` to `SignUp `Screen.**

 ***

- so we will redirect people to sign in screen by providing sign in fragment in setFragemnt method:
 >setFragement(new SignInFragment());
 ***

  # Now coming back to `SignInFragment.java` file:
 and remove all the unnecessary lines here and final code after all the line removal will look like :
 ```
 public class SigninFragment extends Fragment {

    public SigninFragment() {
        // Required empty public constructor
    }

    @Override
    public void onViewCreated(@NonNull View view, @Nullable Bundle savedInstanceState) {
        super.onViewCreated(view, savedInstanceState);

      }
 ```
 ***

 - and we will assign `dont have an account` textview with a variable and find its id :
 > donthaveanaccount = view.findViewById(R.id.tv_dont_have_an_account);

 ***

- Go to onCreate Method and change the return to View because **we will retreieve id's corresponding by view method**

apply the code:
```
View view =  inflater.inflate(R.layout.fragment_signin, container, false);
        donthaveanaccount = view.findViewById(R.id.tv_dont_have_an_account);
        return view;
```
***

- Now we will create a new Method `onViewCreated` and call using `clickListener`

code as follows:
```
@Override
    public void onViewCreated(@NonNull View view, @Nullable Bundle savedInstanceState) {
        super.onViewCreated(view, savedInstanceState);

        donthaveanaccount.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                setFragement(new SignUpFragment());
            }
        });
    }
```
pass the `setFragement()`; method here as shown above &#8593;

***

- After Creating `setFragemnt()` method start `FragmentTransaction` there code as follows:

```
private void setFragement(Fragment fragement) {
        FragmentTransaction fragmentTransaction = getActivity().getSupportFragmentManager().beginTransaction();
        fragmentTransaction.replace(parentframeLayout.getId(),fragement);
        fragmentTransaction.commit();
    }
```
***
 - Pass `frameLayout` in above &#8593; Method; but before that define `frameLayout` in `SignInFragment` as:
 >private FrameLayout frameLayout; _(below public method)_

 Now Assign it in onCreate Method as:
 >frameLayout = getActivity().findViewById(R.id.register_frame_layout);

 ***getActivity() :beause this `SignInFragment `is a `fragement` and not `activity`***

 ***

 - Now coming back to `setFragemnt` method and pass `(new SignUpFragment())`
 because we want user to go to `SignInFragment` when he/she clicks `donthaveanaccount`
 code as follows:
 ```
 public SigninFragment() {
        // Required empty public constructor
    }
    private TextView donthaveanaccount;
    (Added:) private FrameLayout parentframeLayout;

 ```

 ```
 @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        View view =  inflater.inflate(R.layout.fragment_signin, container, false);
        donthaveanaccount = view.findViewById(R.id.tv_dont_have_an_account);
        (Added:)parentframeLayout = getActivity().findViewById(R.id.register_frame_layout);
        return view;

    }
 ```
***
 ```
 @Override
   public void onViewCreated(@NonNull View view, @Nullable Bundle savedInstanceState) {
       super.onViewCreated(view, savedInstanceState);

       donthaveanaccount.setOnClickListener(new View.OnClickListener() {
           @Override
           public void onClick(View v) {
               setFragement(new SignUpFragment());
                                     ↳(Added:)
           }
       });
   }
 ```
***
 ```
 private void setFragement(Fragment fragement) {
       FragmentTransaction fragmentTransaction = getActivity().getSupportFragmentManager().beginTransaction();
       fragmentTransaction.replace(parentframeLayout.getId(),fragement);
       fragmentTransaction.commit();
   }
 ```
***
 # Run you app and you will find no Animation :
 ## So to create Animation :

 **Go to res ➜ rightclick ➜ Create New Anim Directory ➜ create 4 anim files in that directory ➜ slide_from_right, slide_from_left, slideout_from_right, slideout_from_left**

 Follow the attributes :

 **slide_from_right :**
 ```
 <?xml version="1.0" encoding="utf-8"?>
 <set xmlns:android="http://schemas.android.com/apk/res/android"
     android:duration="250"
     android:interpolator="@android:anim/accelerate_decelerate_interpolator">

     <translate android:fromXDelta="100%"
         android:fromYDelta="0%"
         android:toXDelta="0%"
         android:toYDelta="0%"/>

 </set>
 ```
**slide_from_left :**
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="250"
    android:interpolator="@android:anim/accelerate_decelerate_interpolator">

    <translate android:fromXDelta="-100%"
        android:fromYDelta="0%"
        android:toXDelta="-100%"
        android:toYDelta="0%"/>

</set>
```
**slideout_from_left :**
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="250"
    android:interpolator="@android:anim/accelerate_decelerate_interpolator">

    <translate android:fromXDelta="100%"
        android:fromYDelta="0%"
        android:toXDelta="0%"
        android:toYDelta="-100%"/>

</set>
```
**slideout_from_right :**
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="250"
    android:interpolator="@android:anim/accelerate_decelerate_interpolator">

    <translate android:fromXDelta="0%"
        android:fromYDelta="0%"
        android:toXDelta="0%"
        android:toYDelta="100%"/>

</set>
```
***
- After creating Animations lets assign it to `SignInFragment `and `SignUpFragment` :

**SignInFragment:**
In the ***setFragement()*** method :


 >fragmentTransaction.setCustomAnimations(R.anim.slide_from_right, R.anim.slideout_from_left);(Add this line)

**SignUpFragment:**
In the ***setFragement()*** method :

>fragmentTransaction.setCustomAnimations(R.anim.slide_from_left, R.anim.slideout_from_right);(Add this line)
***

Now Overall `setFragement` method will look like :
`SignInFragment`:
```
private void setFragement(Fragment fragement) {
        FragmentTransaction fragmentTransaction = getActivity().getSupportFragmentManager().beginTransaction();
        fragmentTransaction.replace(parentframeLayout.getId(),fragement);
        fragmentTransaction.setCustomAnimations(R.anim.slide_from_right, R.anim.slideout_from_left);
        fragmentTransaction.commit();
    }
```
***
`SignUpFragment`:
```
private void setFragemet(Fragment fragemet) {
        FragmentTransaction fragmentTransaction = getActivity().getSupportFragmentManager().beginTransaction();
        fragmentTransaction.replace(parentFrameLayout.getId(), fragemet);
        fragmentTransaction.setCustomAnimations(R.anim.slide_from_left, R.anim.slideout_from_right);
        fragmentTransaction.commit();
    }
```
***
### Overall SignInFragment:
```
package com.aips.amit.amite_commerceapp;

import android.os.Bundle;

import androidx.annotation.NonNull;
import androidx.annotation.Nullable;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentTransaction;

import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.FrameLayout;
import android.widget.TextView;

public class SigninFragment extends Fragment {

    public SigninFragment() {
        // Required empty public constructor
    }
    private TextView donthaveanaccount;
    private FrameLayout parentframeLayout;


    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        View view =  inflater.inflate(R.layout.fragment_signin, container, false);
        donthaveanaccount = view.findViewById(R.id.tv_dont_have_an_account);
        parentframeLayout = getActivity().findViewById(R.id.register_frame_layout);
        return view;

    }

    @Override
    public void onViewCreated(@NonNull View view, @Nullable Bundle savedInstanceState) {
        super.onViewCreated(view, savedInstanceState);

        donthaveanaccount.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                setFragement(new SignUpFragment());
            }
        });
    }

    private void setFragement(Fragment fragement) {
        FragmentTransaction fragmentTransaction = getActivity().getSupportFragmentManager().beginTransaction();
        fragmentTransaction.replace(parentframeLayout.getId(),fragement);
        fragmentTransaction.setCustomAnimations(R.anim.slide_from_right, R.anim.slideout_from_left);
        fragmentTransaction.commit();
    }
}
```
***
###Overall SignUpFragment:
```
package com.aips.amit.amite_commerceapp;

import android.os.Bundle;

import androidx.annotation.NonNull;
import androidx.annotation.Nullable;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentTransaction;

import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Button;
import android.widget.EditText;
import android.widget.FrameLayout;
import android.widget.ProgressBar;
import android.widget.TextView;

public class SignUpFragment extends Fragment {


    public SignUpFragment() {
        // Required empty public constructor
    }

    private TextView alreadyhaveanaccount;
    private FrameLayout parentFrameLayout;


    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        View view =  inflater.inflate(R.layout.fragment_sign_up, container, false);


        alreadyhaveanaccount = view.findViewById(R.id.tv_already_have_an_account);
        parentFrameLayout = getActivity().findViewById(R.id.register_frame_layout);

        return view;
    }

    @Override
    public void onViewCreated(@NonNull View view, @Nullable Bundle savedInstanceState) {
        super.onViewCreated(view, savedInstanceState);
        alreadyhaveanaccount.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                setFragemet(new SigninFragment());
            }
        });
    }

    private void setFragemet(Fragment fragemet) {
        FragmentTransaction fragmentTransaction = getActivity().getSupportFragmentManager().beginTransaction();
        fragmentTransaction.replace(parentFrameLayout.getId(), fragemet);
        fragmentTransaction.setCustomAnimations(R.anim.slide_from_left, R.anim.slideout_from_right);
        fragmentTransaction.commit();
    }
}
```
‎‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎    ‎       ***-------------------<ins>PART - III</ins> ------------------***
  ‎ ‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎  ‎‎‎‎‎‎‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎  ‎ ‎‎‎  ‎ ‎‎   ‎ ‎

  # Part 4 : [Adding Firebase to Our App in Android Studio](https://youtu.be/r12JRZmTxyA)
  - Go to [FirebaseConsole](https://console.firebase.google.com/u/0/?pli=1) and if hadn't signed in , first sign in to `Google` and then proceed with the above link

  ***

  -  Click on `add` button/icon and `Enter Your Project Name` as in my case its `eCommerce App`

  ***

  - Now click on `Continue` on the next Screen as well and in the 3rd screen select `Default Account for Firebase` in the `drop down box` shown and again click on `Continue`

  ***

  - After finishing up , come to Your **Android Studio** and Copy the `application id` mentioned in the top of any of the activities which you have created
  ***

  - `Nickname` and `debug id` is optional , so skipping that click on **`Register`** App

  ***

  - Download the **`GoogleServices.json`** file , copy the `json` file ,now, come to android studio and from the top right corner change the directory from app to project and paste it in App folder created there.

  ***

  Now come to
  `build.gradle(Project part)`: add this line in **dependencies**:
  >classpath 'com.google.gms:google-services:4.3.5'

  `build.gradle(Module part)`: add this line after **dependencies**
  >apply plugin: 'com.google.gms.google-services'

  Now for all the dependencies :
  add theselines:
  ```
  dependencies {

      implementation 'androidx.appcompat:appcompat:1.0.0'
      implementation 'androidx.constraintlayout:constraintlayout:1.1.3'
      implementation 'androidx.legacy:legacy-support-v4:1.0.0'
      testImplementation 'junit:junit:4.+'
      androidTestImplementation 'androidx.test.ext:junit:1.1.1'
      androidTestImplementation 'androidx.test.espresso:espresso-core:3.1.0'
      implementation 'com.google.android.material:material:1.0.0'
      implementation 'com.google.firebase:firebase-core:11.8.0'
      implementation 'com.google.firebase:firebase-database:11.8.0'
      implementation 'com.google.firebase:firebase-storage:11.8.0'
      implementation 'com.google.firebase:firebase-auth:11.8.0'
      implementation 'com.google.android.material:material:1.0.0'
      implementation 'com.firebaseui:firebase-ui-database:3.2.2'
      implementation 'com.google.firebase:firebase-firestore:11.8.0'
  }
  ```


  **`Overall Build.gradle(Module Part)` coding :**
  ```
  plugins {
      id 'com.android.application'
  }

  android {
      compileSdkVersion 30
      buildToolsVersion "30.0.3"

      defaultConfig {
          applicationId "com.aips.amit.amite_commerceapp"
          minSdkVersion 22
          targetSdkVersion 30
          versionCode 2021
          versionName '2021.2.19e230+cfg'

          testInstrumentationRunner 'androidx.test.runner.AndroidJUnitRunner'
      }

      buildTypes {
          release {
              minifyEnabled false
              proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
              versionNameSuffix '2021.2.19e230+cfg'
          }
          debug {
              versionNameSuffix '2021.2.19e230+cfg'
          }
      }
      compileOptions {
          sourceCompatibility JavaVersion.VERSION_1_8
          targetCompatibility JavaVersion.VERSION_1_8
      }
      flavorDimensions
  }

  dependencies {

      implementation 'androidx.appcompat:appcompat:1.0.0'
      implementation 'androidx.constraintlayout:constraintlayout:1.1.3'
      implementation 'androidx.legacy:legacy-support-v4:1.0.0'
      testImplementation 'junit:junit:4.+'
      androidTestImplementation 'androidx.test.ext:junit:1.1.1'
      androidTestImplementation 'androidx.test.espresso:espresso-core:3.1.0'
      implementation 'com.google.android.material:material:1.0.0'
      implementation 'com.google.firebase:firebase-core:11.8.0'
      implementation 'com.google.firebase:firebase-database:11.8.0'
      implementation 'com.google.firebase:firebase-storage:11.8.0'
      implementation 'com.google.firebase:firebase-auth:11.8.0'
      implementation 'com.google.android.material:material:1.0.0'
      implementation 'com.firebaseui:firebase-ui-database:3.2.2'
      implementation 'com.google.firebase:firebase-firestore:11.8.0'
  }
  apply plugin: 'com.google.gms.google-services'
  ```

  **`Overall Build.gradle(Project Part)`** **coding :**
  ```
  // Top-level build file where you can add configuration options common to all sub-projects/modules.
  buildscript {
      repositories {
          google()
          jcenter()
      }
      dependencies {
          classpath "com.android.tools.build:gradle:4.1.1"
          classpath 'com.google.gms:google-services:4.3.5'

          // NOTE: Do not place your application dependencies here; they belong
          // in the individual module build.gradle files
      }
  }

  allprojects {
      repositories {
          google()
          jcenter()
      }
  }

  task clean(type: Delete) {
      delete rootProject.buildDir
  }
  ```
   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎    ‎    ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎    ‎    ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎    ‎       ***-------------------<ins>PART - IV</ins> ------------------***
   # PART 5 : [COMPLETING WITH REGISTERATION PROCESS](https://youtu.be/olw9sGE0AGo)

   In this video we will verify the user entered `email` with emailPattern and also we will match the `passwords` entered in `password` and `confirm password`with minumum of 8 characters field , not only that we will also see **how we can register user in Firebase using firebase auth and create their account**.
   ***


   Step 1 : Create a new Activity (say `HomeActivity.java`) to send User after Successful Registration to our App.
   ***

   Step 2 : Coming to `SignUpFragment.java` and declare below `public signInFragment(){
     //constructor
     }`
   ```
       private TextView alreadyhaveanaccount;
       private FrameLayout parentFramelayout;
       private EditText signup_email;
       private EditText signup_passwrd;
       private EditText username;
       private EditText confpassword;

       private ImageButton closebtn;
       private Button signup_btn;

       private ProgressBar progressBar;
   ```
   ***
   Step 3 : Assign with their Ids in `onCreateView` Method:
   ```
           alreadyhaveanaccount = view.findViewById(R.id.tv_already_have_an_account);

           parentFramelayout = getActivity().findViewById(R.id.register_frame_layout);

           signup_email = view.findViewById(R.id.sign_up_email);
           signup_passwrd = view.findViewById(R.id.sign_up_password);
           username = view.findViewById(R.id.sign_up_name);
           confpassword = view.findViewById(R.id.sign_up_confirm_password);

           signup_btn = view.findViewById(R.id.sign_up_btn);
           closebtn = view.findViewById(R.id.sign_up_close_btn);

           progressBar = view.findViewById(R.id.sign_up_progress_bar);
   ```
   ***

   Step 4 :Now in the `OnViewCreated()` Method, set a `OnClickListener`
   as follows:
   ```
   signup_btn.setOnClickListener(new View.OnClickListener() {
               @Override
               public void onClick(View v) {
                   //to do
               }
           });
   ```
   ***

   Step 5 : Lets Disable the button because we want to confirm whether the user has inputted correct value or not !!

   - coming to `SignUpFragment.xml` file,
   so lets define first enabled attribute
   >android:enabled = "false"

   >android:textColor="#50ffffff"

   here **50** : `Transparency`
   ***
   Step 6 : Now coming back to `SignUpFragment.java` and check for `userinputs` are correct or not by adding a `addTextChangedListener` to the `EditText` !!
   ```
   signup_email.addTextChangedListener(new TextWatcher() {
               @Override
               public void beforeTextChanged(CharSequence s, int start, int count, int after) {
                   //this will be called when user hasnt inputted anything**dont need tis**
               }

               @Override
               public void onTextChanged(CharSequence s, int start, int before, int count) {
                   checkInputs();
               }

               @Override
               public void afterTextChanged(Editable s) {
                   //this will be called when user has already filled the value */*/dont need this*/
               }
           });
   username.addTextChangedListener(new TextWatcher() {
               @Override
               public void beforeTextChanged(CharSequence s, int start, int count, int after) {
                   //..
               }

               @Override
               public void onTextChanged(CharSequence s, int start, int before, int count) {
                   checkInputs();
               }

               @Override
               public void afterTextChanged(Editable s) {
                   //..
               }
           });
   signup_passwrd.addTextChangedListener(new TextWatcher() {
               @Override
               public void beforeTextChanged(CharSequence s, int start, int count, int after) {
                   //.
               }

               @Override
               public void onTextChanged(CharSequence s, int start, int before, int count) {
                   checkInputs();
               }

               @Override
               public void afterTextChanged(Editable s) {
                   //.
               }
           });
   confpassword.addTextChangedListener(new TextWatcher() {
               @Override
               public void beforeTextChanged(CharSequence s, int start, int count, int after) {
                   //.
               }

               @Override
               public void onTextChanged(CharSequence s, int start, int before, int count) {
                   checkInputs();
               }

               @Override
               public void afterTextChanged(Editable s) {
                   //.
               }
           });
   ```

   **NOTE :** **We dont require to give inputs or assign methods to `afterTextChanged` and `beforeTextChanged` because those two methods will remain unacessible**


   Step 7 : Create Method `checkInputs()`:

   ```
   private void checkInputs() {
          if(!TextUtils.isEmpty(signup_email.getText()))
          {
              if(!TextUtils.isEmpty(username.getText()))
              {
                  if(!TextUtils.isEmpty(signup_passwrd.getText()) && signup_passwrd.length()>=8)
                  {
                      if(!TextUtils.isEmpty(confpassword.getText()))
                      {
                          signup_btn.setEnabled(true);
                          signup_btn.setTextColor(Color.rgb(255,255,255));
                      }else{
                          signup_btn.setEnabled(false);
                          signup_btn.setTextColor(argb(50,255,255,255));
                      }
                  }else
                      {
                          signup_btn.setEnabled(false);
                          signup_btn.setTextColor(argb(50,255,255,255));
                  }
              }
              else{
                  signup_btn.setEnabled(false);
                  signup_btn.setTextColor(argb(50,255,255,255));
              }
          }
          else
              {
                  signup_btn.setEnabled(false);
                  signup_btn.setTextColor(argb(50,255,255,255));
          }
      }
   ```
   ***
   ***
   ***
     Now lets first define our `emailPattern` so as we can match userentered `email` with our `emailPattern`
   >private String emailPattern = "[a-zA-Z0-9._-]+@[a-z]+.[a-z]+";

   - Now coming to `OnViewCreated` Method:

   set `signup_btn` -> `click Listener`
   Code :
   ```
   signup_btn.setOnClickListener(new View.OnClickListener() {
               @Override
               public void onClick(View v) {
                   checkEmailPassword();
               }
           });
   ```

   - Create New Method: **`checkEmailPassword`**

   and check for `email` for matching its **`pattern`**
   code:

   ```
   if(signup_email.getText().toString().matches(emailPattern)){

   }else{

   }
   ```

   - Now check for password confirmation: if the email is confirmed then:
   ```
   if(signup_email.getText().toString().matches(emailPattern))
           {
               if(signup_passwrd.getText().toString().equals(confpassword.getText().toString()))
               {
               }else{

               }else{

               }
   ```

   - and if `password` and `email` pattern matches with its correspondence

   then go ahead and ***`Register or create account using firebase`*** and making use of `progress bar `
   code:
   ```
   private void checkEmailPassword() {

           if(signup_email.getText().toString().matches(emailPattern))
           {
               if(signup_passwrd.getText().toString().equals(confpassword.getText().toString()))
               {

                   progressBar.setVisibility(View.VISIBLE);
                   signup_btn.setEnabled(false);
                   signup_btn.setTextColor(Color.argb(50,255,255,255));
                   fireb.createUserWithEmailAndPassword(signup_email.getText().toString(),signup_passwrd.getText().toString()).addOnCompleteListener(new OnCompleteListener<AuthResult>() {
                       @Override
                       public void onComplete(@NonNull Task<AuthResult> task) {
                           if(task.isSuccessful())
                           {
                               Toast.makeText(getActivity(), "Registered Sucessful", Toast.LENGTH_SHORT).show();
                               semdUserToHomeActivity();
                           }
                           else
                           {
                               signup_btn.setEnabled(true);
                               signup_btn.setTextColor(Color.rgb(255,255,255));
                               progressBar.setVisibility(View.INVISIBLE);
                               String message = task.getException().toString();
                               Toast.makeText(getActivity(), message, Toast.LENGTH_SHORT).show();
                           }
                       }
                   });
               }else{
                   confpassword.setError("Password did not match");
                   confpassword.requestFocus();
               }
           }else{
               signup_email.setError("Enter Valid Email..!");
               signup_email.requestFocus();
           }
   }
   ```
   ---
   # Run the App to check Registration of User to your app

   Next will be on ***Login***
   ---
   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎    ‎    ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎    ‎    ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎   ‎ ‎    ‎        ***-------------------<ins>PART - V</ins> ------------------***
   
   # Part - 6
***

In this video we will verify the user entered `email` and also we will match the `passwords` entered in `password` and `confirm password` field , not only that we will also see **how we can register user in Firebase using firebase auth and create their account**.
***

Continuing from the 4th Video , first of all wr will define email pattern

>private String emailPattern = "[a-zA-Z0-9._-]+@[a-z]+.[a-z]+";

- Now coming to `OnViewCreated` Method:

set `signup_btn` -> `click Listener`
Code :
```
signup_btn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                checkEmailPassword();
            }
        });
```

- Create New Method: **`checkEmailPassword`**

and check for `email` for matching its **`pattern`**
code:

```
if(signup_email.getText().toString().matches(emailPattern)){

}else{

}
```

- Now check for password confirmation: if the email is confirmed then:
```
if(signup_email.getText().toString().matches(emailPattern))
        {
            if(signup_passwrd.getText().toString().equals(confpassword.getText().toString()))
            {
            }else{

            }else{

            }
```

- and if `password` and `email` pattern matches with its correspondence

then go ahead and ***`Register or create account using firebase`*** and making use of `progress bar `
code:
```
private void checkEmailPassword() {

        if(signup_email.getText().toString().matches(emailPattern))
        {
            if(signup_passwrd.getText().toString().equals(confpassword.getText().toString()))
            {

                progressBar.setVisibility(View.VISIBLE);
                signup_btn.setEnabled(false);
                signup_btn.setTextColor(Color.argb(50,255,255,255));
                fireb.createUserWithEmailAndPassword(signup_email.getText().toString(),signup_passwrd.getText().toString()).addOnCompleteListener(new OnCompleteListener<AuthResult>() {
                    @Override
                    public void onComplete(@NonNull Task<AuthResult> task) {
                        if(task.isSuccessful())
                        {
                            Toast.makeText(getActivity(), "Registered Sucessful", Toast.LENGTH_SHORT).show();
                            semdUserToHomeActivity();
                        }
                        else
                        {
                            signup_btn.setEnabled(true);
                            signup_btn.setTextColor(Color.rgb(255,255,255));
                            progressBar.setVisibility(View.INVISIBLE);
                            String message = task.getException().toString();
                            Toast.makeText(getActivity(), message, Toast.LENGTH_SHORT).show();
                        }
                    }
                });
            }else{
                confpassword.setError("Password did not match");
                confpassword.requestFocus();
            }
        }else{
            signup_email.setError("Enter Valid Email..!");
            signup_email.requestFocus();
        }
}
```
---
# Run the App to get result

See you on Login Screen
---

