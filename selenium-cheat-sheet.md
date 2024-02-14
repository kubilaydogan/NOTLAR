# 🇹🇷🇹🇷 Selenium 🇹🇷🇹🇷

---

[//]: # (<ul>)

[//]: # (    <li><a href="">Wait</a></li>)

[//]: # (    <li><a href="#JavascriptExecutor">JavascriptExecutor</a></li>)

[//]: # (    <li><a href="#alert">Alert</a></li>)

[//]: # (    <li><a href="#actions">Actions Class</a></li>)

[//]: # (    <li><a href="#select">Select Class </a></li>)

[//]: # (    <li><a href="#iframes">iframes</a></li>)

[//]: # (    <li><a href="#windows">Windows / tabs</a></li>)

[//]: # (</ul>)



| <a href="#wait"> Wait </a> | <a href="#javascriptExecutor">JavascriptExecutor</a> | <a href="#windows">Windows / tabs</a> | 
|----------------------------|------------------------------------------------------|---------------------------------------|

| <a href="#select">Select Class </a> | <a href="#actions">Actions Class</a>|<a href="#alert">Alert</a>| <a href="#iframes">iframes</a> |
|-|-| -| -|
---

<h2 id="wait">Wait 📌</h2>

### 🌀`Implicit Wait`
```jql
driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(20));
```
### 🌀`Explicit Wait`
```jql
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(20));
wait.until(ExpectedConditions.visibilityOf(webElement));
```

> Some ExpectedConditions
* elementToBeClickable
* visibilityOf
* invisibilityOf
* alertIsPresent
* stalenessOf
* frameToBeAvailableAndSwitchToIt

### 🌀`Fluent Wait`
```jql
Wait<WebDriver> wait = new FluentWait<>(driver)
                .withTimeout(Duration.ofSeconds(30))
                .pollingEvery(Duration.ofSeconds(5))
                .ignoring(NoSuchElementException.class);
```

<h2 id="javascriptExecutor">JavascriptExecutor 📌</h2>

```java
JavascriptExecutor js = JavascriptExecutor(driver);
```
#### ⚠️ Scroll and Click
```java
js.executeScript("arguments[0].scrollIntoView(true);", element);
js.executeScript("arguments[0].click();", element);
// or
js.executeScript(“document.getElementByID('...').click();”);
```
#### ⚠️ Send text (instead of .sendKeys() )
```java
js.executeScript("document.getElementById('..').value='myInput';");
```
#### ⚠️ Get text using JavascriptExecutor
```java
String text = (String) js.executeScript("return document.getElementById('..').value=");
```

#### ⚠️ Interact with checkbox
```java
js.executeScript(“document.getElementByID(‘element id ’).checked=false;”);
```

#### ⚠️ Refresh the browser
```java
js.executeScript(“location.reload()”);
```

<h2 id="alert">Alert 📌</h2>

```java
Alert alert = driver.switchTo().alert();

alert.accept();
alert.dismiss();
alert.getText();
alert.sendKeys("...");
```
🧨 wait.until(ExpectedConditions.**alertIsPresent()**);

<h2 id="actions">Actions Class 📌</h2>

```java
Actions action = new Actions(driver);

*** Hovering ***
action.moveToElement().click().perform();

action.doubleClick()
      .pause(Duration.ofSeconds(3))
      .keyDown(Keys.SHIFT)
      .sendKeys("lowercase" + Keys.ENTER)
      .perform();
```

#### ⚠️ Right Click
```java
action.contextClick()
        .sendKeys(Keys.ARROW_DOWN)
        .sendKeys(Keys.ARROW_DOWN)
        .sendKeys(Keys.ENTER)
        .perform();
```
<h2 id="select">Select Class 📌</h2>

```java
Select select = new Select(element);

select.selectByVisibleText("...");
select.selectByIndex(int);
select.selectByValue("...");

select.deselectByVisibleText("...");
select.deselectByIndex(int);
select.deselectByValue("...");
select.deselectAll();

String str = select.getFirstSelectedOption().getText();

List<WebElement> list = select.getAllSelectedOptions();
List<WebElement> list = select.getOptions();

boolean b = select.isMultiple();
```
<h2 id="iframes">iframes 📌</h2>

```java
driver.switchTo().frame(index);
driver.switchTo().frame("id" or "name");
driver.switchTo().frame(element);
```
```java
driver.switchTo().parentFrame();       // one level top
driver.switchTo().defaultContent();    // to main body
```

<h2 id="windows">Windows / tabs 📌</h2>

#### 🍏 Store the ID of the original window
```java
String mainWindow = driver.getWindowHandle();
```
#### 🍏 Check the count of windows
```java
assertTrue(driver.getWindowHandles().size() == 1);
```
#### 🍏 Wait for the new window or tab
```java
wait.until(ExpectedConditions.numberOfElementsToBe(2));
```
#### 🍏 Loop through until we find a new window handle
```java
for (String windowHandle : driver.getWindowHandles()) {
    if(!originalWindow.contentEquals(windowHandle)) {
        driver.switchTo().window(windowHandle);
        break;
    }
}
```
#### 🍏 Close the tab or window
```java
driver.close();
```
#### 🍏 Switch back to the old tab or window
```java
driver.switchTo().window(originalWindow);
```

#### 🔥 Create new window/tab and switch 🔥

> Note: This feature works with Selenium 4 and later versions

```java
// Opens a new tab and switches to new tab
driver.switchTo().newWindow(WindowType.TAB);

// Opens a new window and switches to new window
driver.switchTo().newWindow(WindowType.WINDOW);
```