## Ex.No:9 Develop a simple calculator using android studio.
## AIM:
To develop a program to develop a simple calculator in Android Studio.

## EQUIPMENTS REQUIRED:
Android Studio(Latest Version)

## ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as calculator and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout using UI components in activity_main.xml.

Step 6: Display the calculator operation in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
/*
```
Program to print the text “calculator operation”.
Developed by: Mohamed S.KEERTHIVASAN
Registeration Number :212222040076
```
*/
## activity_main.xml:
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    android:background="#121212"
    tools:context=".MainActivity">

    <!-- Title Text -->
    <TextView
        android:id="@+id/titleTextView"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Calculator"
        android:textSize="36sp"
        android:textColor="#FFFFFF"
        android:textStyle="bold"
        android:gravity="center"
        android:layout_marginTop="80dp"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

    <!-- First Number Input -->
    <EditText
        android:id="@+id/num1"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:hint="Enter Number 1"
        android:textColor="#FFFFFF"
        android:textColorHint="#B0B0B0"
        android:textSize="18sp"
        android:inputType="number"
        android:padding="16dp"
        android:background="@drawable/edit_text_bg"
        app:layout_constraintTop_toBottomOf="@+id/titleTextView"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="40dp" />

    <!-- Second Number Input -->
    <EditText
        android:id="@+id/num2"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:hint="Enter Number 2"
        android:textColor="#FFFFFF"
        android:textColorHint="#B0B0B0"
        android:textSize="18sp"
        android:inputType="number"
        android:padding="16dp"
        android:background="@drawable/edit_text_bg"
        app:layout_constraintTop_toBottomOf="@+id/num1"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="24dp" />

    <!-- Result TextView -->
    <TextView
        android:id="@+id/result"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Result"
        android:textColor="#FF4081"
        android:textSize="24sp"
        android:gravity="center"
        app:layout_constraintTop_toBottomOf="@+id/num2"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="40dp"/>

    <!-- Sum Button -->
    <Button
        android:id="@+id/sum"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="+"
        android:textSize="24sp"
        android:textColor="#FFFFFF"
        android:backgroundTint="#6200EE"
        android:onClick="doSum"
        app:layout_constraintTop_toBottomOf="@+id/result"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="32dp"
        android:padding="16dp"
        android:layout_marginBottom="8dp"/>

    <!-- Subtraction Button -->
    <Button
        android:id="@+id/sub"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="-"
        android:textSize="24sp"
        android:textColor="#FFFFFF"
        android:backgroundTint="#6200EE"
        android:onClick="doSub"
        app:layout_constraintTop_toBottomOf="@+id/sum"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="16dp"
        android:padding="16dp"
        android:layout_marginBottom="8dp"/>

    <!-- Multiplication Button -->
    <Button
        android:id="@+id/mul"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="×"
        android:textSize="24sp"
        android:textColor="#FFFFFF"
        android:backgroundTint="#6200EE"
        android:onClick="doMul"
        app:layout_constraintTop_toBottomOf="@+id/sub"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="16dp"
        android:padding="16dp"
        android:layout_marginBottom="8dp"/>

    <!-- Division Button -->
    <Button
        android:id="@+id/div"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="÷"
        android:textSize="24sp"
        android:textColor="#FFFFFF"
        android:backgroundTint="#6200EE"
        android:onClick="doDiv"
        app:layout_constraintTop_toBottomOf="@+id/mul"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="16dp"
        android:padding="16dp"
        android:layout_marginBottom="8dp"/>

</androidx.constraintlayout.widget.ConstraintLayout>

```
## MainActivity.java:
```java
package com.example.ex_9;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.text.TextUtils;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {
    EditText e1, e2;
    TextView t1;
    int num1, num2;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize views once here
        e1 = findViewById(R.id.num1);
        e2 = findViewById(R.id.num2);
        t1 = findViewById(R.id.result);
    }

    public boolean getNumbers() {
        String s1 = e1.getText().toString().trim();
        String s2 = e2.getText().toString().trim();

        // Check if both inputs are empty
        if (TextUtils.isEmpty(s1) || TextUtils.isEmpty(s2)) {
            t1.setText("Please enter both numbers");
            return false;
        }

        try {
            // Try to parse the numbers
            num1 = Integer.parseInt(s1);
            num2 = Integer.parseInt(s2);
        } catch (NumberFormatException e) {
            // Catch invalid number format
            t1.setText("Invalid number format");
            return false;
        }

        return true;
    }

    public void doSum(View v) {
        if (getNumbers()) {
            int sum = num1 + num2;
            t1.setText(num1 + " + " + num2 + " = " + sum);
        }
    }

    public void doSub(View v) {
        if (getNumbers()) {
            int sub = num1 - num2;
            t1.setText(num1 + " - " + num2 + " = " + sub);
        }
    }

    public void doMul(View v) {
        if (getNumbers()) {
            int mul = num1 * num2;
            t1.setText(num1 + " × " + num2 + " = " + mul);
        }
    }

    public void doDiv(View v) {
        if (getNumbers()) {
            if (num2 == 0) {
                t1.setText("Cannot divide by zero");
                return;
            }
            double div = (double) num1 / num2;
            t1.setText(num1 + " ÷ " + num2 + " = " + div);
        }
    }
}

```
## AndroidManifest.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.ex_9"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Ex9"
        tools:targetApi="31">

        <activity android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

    </application>

</manifest>

```

## edit_text_bg.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <solid android:color="#2C2C2C" />
    <corners android:radius="16dp" />
    <stroke android:color="#FFFFFF" android:width="2dp" />
</shape>

```
## OUTPUT

<img src="https://github.com/user-attachments/assets/605e813e-bd1c-4f2f-9823-d7906f2ca8a6" width="25%">
<img src="https://github.com/user-attachments/assets/f1aacfe9-db0c-4e11-aa4d-54d0e50ee469" width="25%">

## RESULT
Thus a Simple Android Application develop a program to create simple calculator in Android Studio is developed and executed successfully.
