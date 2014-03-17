ADBKeyBoard 
===========


Android Virtual Keyboard Input via ADB

ADBKeyBoard is a virtual keyboard that receives commands from system broadcast intents, which you can send text input using adb.

There is a shell command 'input', which can help you send text input to the Android system. 
<pre>
usage: input [text|keyevent]
  input text <string>
  input keyevent <event_code>
</pre>
  
But you cannot send unicode characters using this command, as it is not designed to use it this way.
<br />
Reference : http://stackoverflow.com/questions/14224549/adb-shell-input-unicode-character
<pre>
e.g.
adb shell input text '你好嗎' 
is not going to work.
</pre>

ADBKeyboard will help in these cases, especially in device automation and testings.

<h1> How to Use</h1>

<ul>
<li>Enable 'ADBKeyBoard' in the Language&Input Settings.</li>
<li>Set it as Default Keyboard OR Select it as the current input method of certain EditText view.</li>
<li>Sending Broadcast intent via Adb or your Android Services/Apps.</li>
</ul>

Usage Example:
<pre>
1. Sending text input
adb shell am broadcast -a ADB_INPUT_TEXT --es msg "你好嗎! Hello!"

2. Sending keyevent code  (67 = KEYCODE_DEL)
adb shell am broadcast -a ADB_INPUT_CODE --ei code 67

3. Sending editor action (2 = IME_ACTION_GO)
adb shell am broadcast -a ADB_EDITOR_CODE --ei code 2
</pre>

KeyEvent Code Ref: http://developer.android.com/reference/android/view/KeyEvent.html

Editor Action Code Ref: http://developer.android.com/reference/android/view/inputmethod/EditorInfo.html

