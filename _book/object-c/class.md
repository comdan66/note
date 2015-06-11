# Object-C 物件筆記

* 所有物件最終皆繼承 NSObject，故一開始就可以使用 alloc、init、new..等方法(method)
* -減號為實體方法，+號為類別方法

基本格式：

```
@interface 物件名稱 : 繼承物件名稱

方法宣告

@end
```
```
@implementation 物件名稱 {
	變數宣告
}

方法宣告

@end
```

## 物件初始化

* 可以參考 C 語言的指標、記憶體配置的部分

```
Class *myClass = [[Class alloc] init];
```
等同

```
Class *myClass;

myClass = [Class alloc];
myClass = [myClass init];
```
等同

```
Class *myClass = [Class new];
```

## 基本範例

範例：

```
@interface User : NSObject

-(void) setAge: (int) a;
-(int) age;

@end
```

```
@implementation User {
	int age;
}

-(void) setAge: (int) a {
	age = a;
}
-(int) age {
	return age;
}

@end
```

```
User *user = [User new];

[user setAge: 10];
int age = [user age];

NSLog (@"User age: %i", age);
```

## 合成存取

在 interface 加入 `@property`，implementation 加入 `@synthesize` 即可。

範例：

```
@interface User : NSObject

@property int age;

@end
```

```
@implementation User

@synthesize age;

@end
```

```
User *user = [User new];

[user setAge: 10];
int age = [user age];

NSLog (@"User age: %i", age);
```

當有設置 setter 以及 getter 後，可以做以下應用：

```
User *user = [User new];

user.age = 10;

NSLog (@"User age: %i", user.age);
```