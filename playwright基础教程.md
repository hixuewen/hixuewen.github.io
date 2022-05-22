## 恢复鉴权状态

### 代码方式

```python
# Save storage state into the file.
storage = context.storage_state(path="state.json")

# Create a new context with the saved storage state.
context = browser.new_context(storage_state="state.json")
```

### UI方式

```bat
# 保存
playwright codegen --save-storage context.json https://movie.douban.com/review/best/

# 加载
playwright codegen --load-storage context.json https://movie.douban.com/review/best/
```

## frame里的元素定位

```python
page.frame_locator("").locator("").click()
```

## 改变浏览器大小

```python
context = browser.new_context(viewport={"width":1920, "height":1080})
```

## 调试

```
# 方法1
page.pause()

# 方法2

```

