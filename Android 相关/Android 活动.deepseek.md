好的，我们来详细、深入地讲解一下 Android 中的“活动”（Activity）。

### 一、什么是活动（Activity）？

**活动（Activity）** 是 Android 应用的一个核心组件，它代表一个单一的、具有用户界面的屏幕。你可以把它想象成 Web 应用中的一个网页，或者桌面应用中的一个窗口。

*   **用户交互的入口**：用户与应用的所有交互都发生在活动中。例如，一个电子邮件应用可能有一个活动显示新邮件列表，另一个活动用来编写邮件，还有一个活动用于阅读邮件。
*   **独立且可组合**：每个活动都是独立的，但它们可以协同工作，共同构成一个统一的用户界面。一个应用通常由多个活动组成。

---

### 二、活动的基本生命周期（Activity Lifecycle）

这是理解活动的重中之重。活动的生命周期是一组状态的变化，系统通过调用一系列的回调方法（Callback Methods）来引导活动在这些状态间转换。你需要在适当的回调方法中执行正确的操作，以确保应用行为符合预期。

生命周期状态主要包括：

1.  **Created（已创建）**：活动被创建，但还不可见。
2.  **Started（已启动）**：活动可见，但还未获得焦点（例如，可能被一个对话框部分遮挡）。
3.  **Resumed（已恢复）**：活动可见并位于前台，用户可以与之交互。这是应用的“运行中”状态。
4.  **Paused（已暂停）**：活动部分可见但失去焦点（例如，屏幕上出现一个非全屏的对话框或透明活动）。活动实例仍在内存中。
5.  **Stopped（已停止）**：活动完全不可见（被另一个活动完全覆盖）。活动实例及其状态信息仍然被保留。
6.  **Destroyed（已销毁）**：活动被系统销毁，所占用的内存将被回收。

为了管理这些状态转换，活动提供了一系列核心回调方法：

| 方法 | 描述 | 通常在此处执行的操作 |
| :--- | :--- | :--- |
| `onCreate()` | **首次创建活动时调用**。这是**必须实现**的方法。 | - 执行基本应用启动逻辑。<br>- **必须调用 `setContentView()`** 来设置布局 UI。<br>- 初始化组件（如绑定视图、设置列表适配器）。<br>- 绑定数据（可能来自 `ViewModel` 或 `onSaveInstanceState`）。 |
| `onStart()` | 活动变得**可见**时调用。 | 启动或恢复那些需要与 UI 保持同步的组件（例如，动画、相机预览）。 |
| `onResume()` | 活动开始与用户**交互**时调用。此时活动位于活动栈的顶部。 | 启动高频率的组件（如传感器监听、音频/视频播放）。 |
| `onPause()` | 当系统**准备**恢复另一个活动时调用。 | 释放高频率的组件或系统资源（如传感器、广播接收器），以节省电量。<br>**注意**：此方法执行要快，因为下一个活动的 `onResume()` 必须等它执行完。 |
| `onStop()` | 活动**完全不可见**时调用。 | 执行重量级的关闭操作（如将数据写入数据库）。 |
| `onDestroy()` | 活动被**销毁前**调用。 | 释放所有未释放的资源，避免内存泄漏。 |
| `onRestart()` | 处于停止状态的活动**重新启动**前调用（即从 `onStop()` 回到 `onStart()`）。 | 执行仅在活动从不可见重新变为可见时才需要的特殊恢复逻辑。 |

**生命周期流程图：**
一个经典的理解方式是记住以下配对：
*   整个生命周期：`onCreate()` → ... → `onDestroy()`
*   可见生命周期：`onStart()` → ... → `onStop()`
*   前台生命周期：`onResume()` → ... → `onPause()`

![Android Activity Lifecycle Diagram](https://developer.android.com/static/images/activity_lifecycle.png)
*(图片来源：Android 开发者官网)*

---

### 三、活动的创建和启动

#### 1. 创建活动（定义类）
你需要创建一个继承自 `Activity`（或其子类，如 `AppCompatActivity`）的 Java/Kotlin 类，并重写关键方法，尤其是 `onCreate`。

**Kotlin 示例：**
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState) // 必须首先调用父类方法
        setContentView(R.layout.activity_main) // 设置布局文件

        // 初始化视图和逻辑
        val button: Button = findViewById(R.id.my_button)
        button.setOnClickListener {
            // 点击按钮后启动另一个活动
            val intent = Intent(this, SecondActivity::class.java)
            startActivity(intent)
        }
    }
}
```

#### 2. 在清单文件中声明（AndroidManifest.xml）
所有活动都必须在 `AndroidManifest.xml` 文件中声明，否则系统无法识别和启动它。你需要指定 `<activity>` 标签。

```xml
<manifest ... >
    <application ... >
        <!-- 主活动，通常作为应用入口 -->
        <activity
            android:name=".MainActivity"
            android:label="@string/app_name">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <!-- 其他活动 -->
        <activity
            android:name=".SecondActivity"
            android:label="@string/title_second_activity" />
    </application>
</manifest>
```
*   `<intent-filter>`：定义了活动如何被启动。`MAIN` 和 `LAUNCHER` 表示这是应用的主入口点，会在启动器中显示图标。

#### 3. 启动活动（使用 Intent）
活动通过 **Intent（意图）** 来启动。Intent 是一个消息对象，用于请求另一个应用组件（如活动）执行操作。

*   **显式 Intent**：明确指定要启动的组件类名。用于启动应用内的活动。
    ```kotlin
    val intent = Intent(this, SecondActivity::class.java)
    startActivity(intent)
    ```

*   **隐式 Intent**：声明要执行的操作（如查看、分享、编辑），让系统决定由哪个应用的活动来处理。用于启动其他应用的活动。
    ```kotlin
    val intent = Intent(Intent.ACTION_VIEW).apply {
        data = Uri.parse("https://www.example.com")
    }
    startActivity(intent)
    ```

---

### 四、活动间的数据传递

#### 1. 向新活动传递数据
使用 Intent 的 `putExtra()` 方法添加数据。

```kotlin
val intent = Intent(this, SecondActivity::class.java).apply {
    putExtra("EXTRA_MESSAGE", "Hello from MainActivity!")
    putExtra("EXTRA_NUMBER", 42)
}
startActivity(intent)
```

#### 2. 从Intent中获取数据
在目标活动（如 `SecondActivity`）的 `onCreate()` 中，通过 `intent` 属性获取传递过来的数据。

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_second)

    val message = intent.getStringExtra("EXTRA_MESSAGE")
    val number = intent.getIntExtra("EXTRA_NUMBER", 0) // 0 是默认值

    // 使用获取到的数据更新 UI
    findViewById<TextView>(R.id.text_view).text = message
}
```

#### 3. 返回数据给上一个活动
有时你需要从启动的活动返回一个结果（例如，用户从通讯录中选择了一个联系人）。

*   **启动活动时请求结果**：使用 `startActivityForResult()`（已弃用）或新的 **Activity Result APIs**（推荐）。

**推荐方式（使用 Activity Result API）：**
1.  在启动方活动中注册对结果的监听：
    ```kotlin
    class MainActivity : AppCompatActivity() {
        // 1. 创建一个 ActivityResultLauncher
        private val startForResult = registerForActivityResult(ActivityResultContracts.StartActivityForResult()) { result ->
            // 3. 当 SecondActivity 返回时，在这里处理结果
            if (result.resultCode == Activity.RESULT_OK) {
                val data: Intent? = result.data
                val returnedData = data?.getStringExtra("return_key")
                // 使用返回的数据
            }
        }

        fun openSecondActivity() {
            val intent = Intent(this, SecondActivity::class.java)
            // 2. 使用 launcher 启动活动，而不是 startActivity
            startForResult.launch(intent)
        }
    }
    ```

2.  在被启动的活动（`SecondActivity`）中设置返回结果：
    ```kotlin
    class SecondActivity : AppCompatActivity() {
        fun setResultAndFinish() {
            val returnIntent = Intent().apply {
                putExtra("return_key", "Some return data")
            }
            setResult(Activity.RESULT_OK, returnIntent) // 设置结果码和返回的 Intent
            finish() // 关闭当前活动，返回给 MainActivity
        }
    }
    ```

---

### 五、任务的返回栈（Back Stack）

Android 系统使用一个“返回栈”来管理用户导航。当用户启动一个新活动时，该活动会被压入栈顶。当用户按下**返回按钮**时，栈顶的活动会被弹出（销毁），用户会回到上一个活动。

*   **父活动声明**：你可以在清单文件中使用 `android:parentActivityName` 属性来指定一个活动的逻辑父活动，这有助于系统在返回时提供一致的导航体验。

---

### 六、活动的启动模式（Launch Mode）

通过清单文件中的 `android:launchMode` 属性或 Intent 标志（Flags），你可以改变活动与任务返回栈的默认关联方式。主要有四种：

1.  **`standard`（默认）**：每次启动都会创建一个新的活动实例。
2.  **`singleTop`**：如果目标活动已经位于栈顶，则不会创建新实例，而是调用其 `onNewIntent()` 方法。适用于防止重复创建同一个活动（如搜索页）。
3.  **`singleTask`**：活动在任务中始终保持只有一个实例。如果已存在，系统会将该活动之上的所有其他活动弹出栈，使其位于栈顶并调用 `onNewIntent()`。
4.  **`singleInstance`**：与 `singleTask` 类似，但该活动会独自占用一个任务，其他活动不能与之共存于同一任务。

---

### 总结

活动是 Android 应用的基石，理解其生命周期、创建、启动、数据传递和启动模式至关重要。

*   **生命周期**是活动的灵魂，确保资源合理使用和应用流畅运行。
*   **Intent** 是活动间通信和启动的桥梁。
*   **返回栈**提供了符合用户预期的导航体验。
*   熟练运用这些概念，你就能构建出结构清晰、行为正确、用户体验良好的 Android 应用。

现代 Android 开发（MAD）中，**Jetpack 库**（如 `ViewModel`、`LiveData`）和**组合式导航**（Navigation Component）极大地简化了状态管理和页面跳转的逻辑，但它们底层仍然建立在活动的基本原理之上。因此，扎实掌握活动是学习更高级框架的前提。
