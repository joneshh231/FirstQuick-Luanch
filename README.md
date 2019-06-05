# FirstQuick-Luanch
A app I created to launch inside and outside the app


// Main activity//

package com.example.loginapp.quicklauncher.com;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.support.v7.app.AppCompatActivity;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);


//Assigning the Button (secondactivity and google) with click, so when i click these bottons an action is going to happen but first i have to set them//


        Button secondactivityBtn = (Button)findViewById(R.id.secondactivitybttn);
        secondactivityBtn. setOnClickListener(new View.OnClickListener() {
        
//when the button secondactivity is pressed it takes you to a different screen where you will se Hello world//

            @Override
            public void onClick(View v) {
               Intent startintent = new Intent(getApplicationContext(), secondactivity.class);
               startintent.putExtra("QuickLauncher.Something","Hello World");
               startActivity(startintent);
            }
        });
        
       
  //when the button google is pressed it will launch you out of the app into the web address google.com//
        
        
        Button googlebttn = (Button)findViewById(R.id.googlebttn);
                googlebttn.setOnClickListener(new View.OnClickListener() {
                    @Override
                    public void onClick(View v) {
                        String google = "http://www.google.com";
                        Uri webaddress = Uri.parse(google);
                        Intent gotoGoogle = new Intent(Intent.ACTION_VIEW, webaddress);
                        if(gotoGoogle.resolveActivity(getPackageManager()) != null){
                            startActivity(gotoGoogle);
                    }
                }
    });
}}

//second activity. Links textview with the string to open google outside of the app//

package com.example.loginapp.quicklauncher.com;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.TextView;

public class secondactivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_secondactivity);

        if (getIntent().hasExtra("QuickLauncher.Something")){
            TextView tv = (TextView)findViewById(R.id.textView);
            String text = getIntent().getExtras().getString("QuickLauncher.Something");
            tv.setText(text);
        }
    }


