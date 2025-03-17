

12. Create an Android application to demonstrate the use of a sub menu. The toast should appear by
selecting the sub menu item.
→
**Create menu file in res/menu folder.

menu_main.xml:

<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:tools="http://schemas.android.com/tools"
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
    <item
        android:id="@+id/menu_cut"
        android:title="Cut"
        android:icon="@drawable/ic_cut"
        app:showAsAction="ifRoom" />
    <item
        android:id="@+id/menu_copy"
        android:title="Copy"
        android:icon="@drawable/ic_copy"
        app:showAsAction="ifRoom" />
    <item
        android:id="@+id/menu_paste"
        android:title="Paste"
        android:icon="@drawable/ic_paste"
        app:showAsAction="ifRoom" />

</menu>

MainActivity.kt:

package com.example.practical
import android.os.Bundle
import android.view.Menu
import android.view.MenuItem
import android.widget.EditText
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
class MainActivity : AppCompatActivity() {
private lateinit var editText: EditText
override fun onCreate(savedInstanceState: Bundle?) {
super.onCreate(savedInstanceState)
setContentView(R.layout.activity_main)
editText = findViewById(R.id.editText)
}
override fun onCreateOptionsMenu(menu: Menu?): Boolean {
menuInflater.inflate(R.menu.menu_main, menu)
return true
}
override fun onOptionsItemSelected(item: MenuItem): Boolean {
when (item.itemId) {
R.id.menu_cut -> {
val cutText = editText.text.toString()
editText.setText("") // Clear the text after cut
Toast.makeText(this, "Cut: $cutText", Toast.LENGTH_SHORT).show()
return true
}
R.id.menu_copy -> {
val copyText = editText.text.toString()
Toast.makeText(this, "Copied: $copyText", Toast.LENGTH_SHORT).show()
return true
}
R.id.menu_paste -> {
val pasteText = "Pasted Text"
editText.append(pasteText)
Toast.makeText(this, "Pasted: $pasteText", Toast.LENGTH_SHORT).show()
return true
}
else -> return super.onOptionsItemSelected(item)
}
}
}

Activity_main.xml:

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:orientation="vertical"
android:padding="16dp"
android:gravity="center">
<EditText
android:id="@+id/editText"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:hint="Type here"
android:padding="16dp"
android:textSize="18sp"
android:layout_marginBottom="20dp"/>
</LinearLayout>
