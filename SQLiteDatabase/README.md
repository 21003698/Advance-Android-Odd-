
# Ex.No:1 To create a database table and to display the database table field using SQLite Database in Android Studio.


## AIM:

To create a database table and to display the database table field using SQLite Database in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as HelloWorld and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Display message give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to print the DatabaseTable using the SQLite”.
Developed by:Challa Sandeep
Registeration Number :212221240011
*/
```
##MainActivity.java

package com.example.sandeep;

import androidx.appcompat.app.AppCompatActivity;

import android.annotation.SuppressLint;
import android.database.Cursor;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {
    EditText editUserID;
    EditText editUserName;
    EditText editUserPassword;

    DatabaseManager dbManager;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        editUserID= findViewById(R.id.editTextID);
        editUserName=findViewById(R.id.editTextUserName);
        editUserPassword=findViewById(R.id.editTextPassword);

        dbManager=new DatabaseManager(this);
        try{
            dbManager.open();
        }
        catch(Exception e){
            e.printStackTrace();
        }
    }


    public void btnInsertPressed(View v){
        dbManager.insert(editUserName.getText().toString(),editUserPassword.getText().toString());
    }

    public void btnFetchPressed(View v){
        Cursor cursor=dbManager.fetch();
        if (cursor.moveToFirst())
        {
            do{
                @SuppressLint("Range") String ID=cursor.getString(cursor.getColumnIndex(DatabaseHelper.USER_ID));
                @SuppressLint("Range") String username=cursor.getString(cursor.getColumnIndex(DatabaseHelper.USER_NAME));
                @SuppressLint("Range") String password=cursor.getString(cursor.getColumnIndex(DatabaseHelper.USER_PASSWORD));
                Log.i("DATABASE_TAG","I have read ID : "+ID+" Username : "+username+" password : "+password);
            }while(cursor.moveToNext());
        }
    }

    public void btnUpdatePressed(View v){
        dbManager.update(Long.parseLong(editUserID.getText().toString()),editUserName.getText().toString(),editUserPassword.getText().toString());
    }

    public void btnDeletePressed(View v){
        dbManager.delete(Long.parseLong(editUserID.getText().toString()));
    }
}
```

## OUTPUT




## RESULT
Thus a Simple Android Application create a dtatabase table and to display the database table  using SQLite Database in Android Studio is developed and executed successfully.
