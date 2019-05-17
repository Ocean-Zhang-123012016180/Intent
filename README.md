# Intent
结果截图


![Image text](https://github.com/Ocean-Zhang-123012016180/Intent/blob/master/image/1.png)


![Image text](https://github.com/Ocean-Zhang-123012016180/Intent/blob/master/image/2.png)





主要代码：

package com.example.intent;


import android.content.Intent;
import android.net.Uri;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {
    private String url;
    Button b1;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        b1=findViewById(R.id.b1);
        b1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent intent=new Intent(Intent.ACTION_VIEW);
                EditText editText1 =(EditText) findViewById (R.id.E1);
                url=editText1.getText().toString();
                intent.putExtra("url",url);
                startActivity(intent);
            }
        });
    }
}



package com.example.webview;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.webkit.WebView;
import android.webkit.WebViewClient;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Intent intent = this.getIntent();
        Bundle bundle = intent.getExtras();

        WebView webView = (WebView)findViewById(R.id.w1);
        webView.getSettings().setJavaScriptEnabled(true);
        webView.setWebViewClient(new WebViewClient());
        if(bundle !=null){
            String url = bundle.getString("url");
            webView.loadUrl(url);
        }
    }
}


