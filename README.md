
# Rapport

Arbetet har gått smidigt och följt de instruktioner som tilldelats inuti "MainActivity.java". En del commits och pushar har gjorts under lite andra delar
än de instruktionerna visar.

- Internet access läggs in i AndroidManifest.xml.
```
<uses-permission android:name="android.permission.INTERNET" />
```
- WebView element tilläggs i content_main, här får den även id:t "my_webview".
```
<WebView
           android:layout_width="match_parent"
           android:layout_height="match_parent"
           android:id="@+id/my_webview"
           />
```
- Privat WebView tilläggs inuti MainActivity.
```
public class MainActivity extends AppCompatActivity {
    private WebView myWebView;
```
- webview och dess id blir tillagd inuti MainActivitys oncreate, samt aktiverar javascript.
```
protected void onCreate(Bundle savedInstanceState) {
        myWebView = findViewById(R.id.my_webview);
        myWebView.getSettings().setJavaScriptEnabled(true);
        WebViewClient webViewClient = new WebViewClient();
        myWebView.setWebViewClient(webViewClient);
}
```
- showExternalWebPage och showInternalWebPage får tillagd de adresser de behöver, dessa kalla även
inuti onOptionsItemSelected.
```
public boolean onOptionsItemSelected(MenuItem item) {
 if (id == R.id.action_external_web) {
            showExternalWebPage();
            Log.d("==>","Will display external web page");
            return true;
        }

        if (id == R.id.action_internal_web) {
            showInternalWebPage();
            Log.d("==>","Will display internal web page");
            return true;
        }
 }
```
- en mapp för assets skapas och inuti den skapas index.html, denna html fil redigeras för
InternalWebPage.
```
<!DOCTYPE html>
 <html lang="en">
 <head>
     <meta charset="UTF-8"/>
     <title>Mokoko Test</title>
 </head>
 <body>
 <h1>bruh</h1>
 <h1>bruh</h1>
 </body>
 </html>
```
Nedan följer hur External och Internal webview ser ut.

![](ScreenshotExternal.png)
![](ScreenshotInternal.png)

