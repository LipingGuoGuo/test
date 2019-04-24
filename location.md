###### WebDriver8种基本元素定位方式
> * 通过id定位 `find_element_by_id`
```
from selenium import webdriver
import time
from selenium.webdriver.common.by import By  ##引用By类

driver = webdriver.Chrome()
driver.implicitly_wait(10)
driver.get("http://www.baidu.com")

driver.find_element_by_id("kw").send_keys("Selenium")
driver.find_element_by_id("su").click()

time.sleep(2）
driver.quit()
```
> * 通过name `find_element_by_name()`
> * 通过class_name `find_element_by_class_name`
```
driver.find_element_by_name("wd").send_keys("Python")
driver.find_element_by_class_name("s_btn").click()
```
> * 通过xpath，可以用来确定xml文档中的元素位置，通过元素的路径来完成对元素的查找；一种是**绝对路径**定位，一种是**利用元素属性**进行xpath定位 `find_element_by_xpath("/html/body/div/div[2]/form/div/div[1]/div")`
> * 通过标签名去定位 `find_element_by_tag_name()`一般一种标签在一个页面不止一次甚至大量出现，定位方式作用不大
> * 通过link_text()或者partial_link_text()定位超链接，即html页面中的<a>标签 `find_element_by_link_text("新闻").click()` `find_element_by_partial_link_text("闻").click()`
##### By定位
```使用前提为导入By类：from selenium.webdriver.common.by import By
find_element(By.ID,"kw")
find_element(By.NAME,"wd")
find_element(By.CLASS_NAME,"s_ipt"）
find_element(By.TAG_NAME,"input")
find_element(By.LINK_TEXT,u'新闻   ')
find_element(By.PARTIAL_LINK_TEXT,u'新')
find_element(By.XPATH,"//*[@class='bg s_btn']")
find_element(By.CSS_SELECTOR,"span.bg s_btn_wr>input#su")
```