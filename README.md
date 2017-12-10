# 使用[Jasmine](http://jasmine.github.io) 测试订阅阅读器项目

## `"RSS Feeds`" 测试用例

1. 编写一个测试遍历 allFeeds 变量被定义了而且不是空的。

```  
 it('are defined', function() {
    expect(allFeeds).toBeDefined();
    expect(allFeeds.length).not.toBe(0);
 });

```

2. 编写一个测试遍历 allFeeds 对象里面的所有的源来保证有链接字段而且链接不是空的。

``` 
it('all url are defined and not empty', function() {
            allFeeds.forEach(function(item) {
                expect(item.url).not.toBeNull();
            });
});
```

3. 编写一个测试遍历 allFeeds 对象里面的所有的源来保证有名字字段而且不是空的。

```
it('all name are defined and not empty', function() {
            allFeeds.forEach(function(item) {
                expect(item.name).not.toBeNull();
            });
});
```

## `"The menu`" 测试用例

1. 编写一个测试用例保证菜单元素默认是隐藏的。
 
2. 判断body标签是否有`".menu-hidden`" class，如果有表示隐藏了。
 
3. 写一个测试用例保证当菜单图标被点击的时候菜单会切换可见状态。
 
```
it('click menu icon hidding can switch', function() {
    $menuIcon.trigger("click");
    expect($body.hasClass('menu-hidden')).toBeFalsy();
    $menuIcon.trigger("click");
    expect($body.hasClass('menu-hidden')).toBeTruthy();
 });
```
判断body标签是否有`".menu-hidden`" class。`"false `"没有，`"true`" 是有。


## `"Initial Entries`"测试用例

1.编写一个测试保证 loadFeed 函数被调用而且工作正常,判断 `".feed `"容器元素
里面有`" .entry `"的元素。使用`"beforeEach()`"和异步的`"done()`"函数。

```
it("There is a loadFeed function, it works", function(done) {
    expect($(".feed .entry").length).not.toBe(0);
    done();
});
```

## `"New Feed Selection`"测试用例

1.编写一个测试保证当用 `loadFeed` 函数加载一个新源的时候内容会真的改变。调用`"loadFeed(3, done)`" 不同的值，使用`"beforeEach()`"和异步的`"done()`"函数。

```
it('The content changed', function(done) {
    expect(content).not.toBe($('.feed').html());
    done();
});
```