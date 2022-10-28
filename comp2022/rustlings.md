rustlings笔记。



# rustlings简介

## 是什么

靠修复语法问题来学语法的rust练习题。

## 练习方法

1. 开启考试 -- rustlings watch -- rustlings会按预定义顺序让你做题并批改。
2. 用户做题
   1. 审题 -- 查看注释
   2. 答题 -- 按要求或提示修正代码，
   3. 交卷 -- 去掉`I AM NOT DONE`注释，rustlings会批改，告诉你错误或让你做下一题目。



## 常用命令

- 进度 -- rustlings list
- 提示 -- rustlings hint name



# Intro

## intro1 - 提交

### 问题

```rust
// I AM NOT DONE
fn main() {
    println!("Hello and");
    println!(r#"       welcome to...                      "#);
    println!(r#"                 _   _ _                  "#);
    println!(r#"  _ __ _   _ ___| |_| (_)_ __   __ _ ___  "#);
    println!(r#" | '__| | | / __| __| | | '_ \ / _` / __| "#);
    println!(r#" | |  | |_| \__ \ |_| | | | | | (_| \__ \ "#);
    println!(r#" |_|   \__,_|___/\__|_|_|_| |_|\__, |___/ "#);
    println!(r#"                               |___/      "#);
    println!();
    println!("This exercise compiles successfully. The remaining exercises contain a compiler");
    println!("or logic error. The central concept behind Rustlings is to fix these errors and");
    println!("solve the exercises. Good luck!");
}
```

### 解决

去掉 `I AM NOT DONE`

## intro2 - 打印

### 问题

```rust
// 打印 Hello world
fn main() {
    println!("Hello {}!");
}
```

### 解决

```rust
// 给println宏传递参数
fn main() {
    println!("Hello {}!", "world");
}
```

# Variables

## variables1 - let绑定

### 问题

```rust
// 错误的变量绑定语法
fn main() {
    x = 5;
    println!("x has the value {}", x);
}
```

### 解决

```rust
// 正确的变量绑定语法
fn main() {
    let x = 5;
    println!("x has the value {}", x);
}
```

## variables2 - 类型信息

### 问题

```rust
fn main() {
    // 变量声明时类型信息缺失
    let x;
    // 变量未初始化就使用
    if x == 10 {
        println!("Ten!");
    } else {
        println!("Not ten!");
    }
}
```

### 解决

```rust
fn main() {
    // 给于类型信息并且初始化
    let x:i32 = 10;
    if x == 10 {
        println!("Ten!");
    } else {
        println!("Not ten!");
    }
}
```

## variables3 - 可变性

### 问题

```rust
fn main() {
    // x被声明为不可变变量
    let x = 3;
    println!("Number {}", x);
    // 写不可变变量
    x = 5; // don't change this line
    println!("Number {}", x);
}
```

### 解决

```rust
fn main() {
    // 将x声明为可变变量
    let mut x = 3;
    println!("Number {}", x);
    x = 5; // don't change this line
    println!("Number {}", x);
}
```

## variables4 - 初始化

### 问题

```rust
fn main() {
    let x: i32;
    // x未初始化不能用
    println!("Number {}", x);
}
```

### 解决

```rust
fn main() {
    let x: i32 = 1;
    // x初始化后可用
    println!("Number {}", x);
}
```

## variables5 - 遮蔽

### 问题

```rust
fn main() {
    let number = "T-H-R-E-E"; // don't change this line
    println!("Spell a Number : {}", number);
    // 不能将数字赋值给&str的number
    number = 3;
    println!("Number plus two is : {}", number + 2);
}
```

### 解决

rust 允许 变量遮蔽（variable shadowing）

```rust
fn main() {
    let number = "T-H-R-E-E"; // don't change this line
    println!("Spell a Number : {}", number);
    // 重新声明一个整型的number来遮蔽旧number
    let number = 3;
    println!("Number plus two is : {}", number + 2);
}
```

## variables6 - 常量

### 问题

```rust
// 常量声明缺少类型信息
const NUMBER = 3;
fn main() {
    println!("Number {}", NUMBER);
}
```

### 解决

```rust
// 常量声明必须包含类型信息
const NUMBER:i32 = 3;
fn main() {
    println!("Number {}", NUMBER);
}
```

# Functions

## functions1 - 声明

### 问题

函数未声明就使用

```rust
fn main() {
    // 当前作用域内找不到call_me
    call_me();
}
```

### 解决

函数得先声明后使用

```rust
fn main() {
    call_me();
}
// 根据call_me签名声明一个函数
fn call_me() {
    
}
```

## functions2 - 参数类型

### 问题

```rust
fn main() {
    call_me(3);
}
// 参数类型缺失
fn call_me(num:i32) {
    for i in 0..num {
        println!("Ring! Call number {}", i + 1);
    }
}
```

### 解决

```rust
fn main() {
    call_me(3);
}
// 补充参数类型
fn call_me(num:i32) {
    for i in 0..num {
        println!("Ring! Call number {}", i + 1);
    }
}
```

## functions3 - 传参

### 问题

```rust
fn main() {
	// 错误传参
    call_me();
}
fn call_me(num:u32) {
    for i in 0..num {
        println!("Ring! Call number {}", i + 1);
    }
}
```

### 解决

```rust
fn main() {
    // 补充参数
    call_me(3);
}
fn call_me(num:u32) {
    for i in 0..num {
        println!("Ring! Call number {}", i + 1);
    }
}
```

## functions4 - 返回值类型

### 问题

```rust
fn main() {
    let original_price = 51;
    println!("Your sale price is {}", sale_price(original_price));
}
// 缺少返回值类型
fn sale_price(price: i32) -> {
    if is_even(price) {
        price - 10
    } else {
        price - 3
    }
}
```

### 解决

```rust
fn main() {
    let original_price = 51;
    println!("Your sale price is {}", sale_price(original_price));
}
// 补充返回值类型
fn sale_price(price: i32) -> i32 {
    if is_even(price) {
        price - 10
    } else {
        price - 3
    }
}
```

## functions5 - 返回

### 问题

```rust
fn main() {
    let answer = square(3);
    println!("The answer is {}", answer);
}

fn square(num: i32) -> i32 {
    // 因为;表示不是尾表达式，并且不是return表达式，所以会返回()，和i32不匹配
    num * num;
}
```

implicitly returns `()` as its body has no tail or `return` expression

### 解决

```rust
fn main() {
    let answer = square(3);
    println!("The answer is {}", answer);
}

fn square(num: i32) -> i32 {
    // 去掉;成为尾表达式
    num * num
}
```

# If

## if1 - 基本分支

### 问题

```rust
pub fn bigger(a: i32, b: i32) -> i32 {
    // Complete this function to return the bigger number!
    // Do not use:
    // - another function call
    // - additional variables
    // Execute `rustlings hint if1` for hints
}

// Don't mind this for now :)
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn ten_is_bigger_than_eight() {
        assert_eq!(10, bigger(10, 8));
    }

    #[test]
    fn fortytwo_is_bigger_than_thirtytwo() {
        assert_eq!(42, bigger(32, 42));
    }
}
```

### 解决

```rust
pub fn bigger(a: i32, b: i32) -> i32 {
    if a > b {
        a
    } else {
        b
    }
}
...
```

## if2 - 默认分支

### 问题

```rust
// 根据输入分支并且有默认分支
pub fn fizz_if_foo(fizzish: &str) -> &str {
    if fizzish == "fizz" {
        "foo"
    } else {
        1
    }
}

// No test changes needed!
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn foo_for_fizz() {
        assert_eq!(fizz_if_foo("fizz"), "foo")
    }

    #[test]
    fn bar_for_fuzz() {
        assert_eq!(fizz_if_foo("fuzz"), "bar")
    }

    #[test]
    fn default_to_baz() {
        assert_eq!(fizz_if_foo("literally anything"), "baz")
    }
}
```

### 解决

```rust
// 按测试结果建立分支
pub fn fizz_if_foo(fizzish: &str) -> &str {
    if fizzish == "fizz" {
        "foo"
    } else if fizzish == "fuzz" {
        "bar"
    } else {
        "baz"
    }
}
```

# Quiz1 - Variables + Functions + If

## 问题

```rust
// 买苹果，40个以下的价格是2元/个，40个以上的价格是1元/个
// 实现计算苹果价格的函数
#[test]
fn verify_test() {
    let price1 = calculate_apple_price(35);
    let price2 = calculate_apple_price(40);
    let price3 = calculate_apple_price(65);

    assert_eq!(70, price1);
    assert_eq!(80, price2);
    assert_eq!(65, price3);
}
```

## 解决

```rust
fn calculate_apple_price(num:i32) -> i32 {
    if num <= 40 {
        2 * num
    } else {
        num
    }
}
```



# 参考

[rust-lang/rustlings](https://github.com/rust-lang/rustlings)

