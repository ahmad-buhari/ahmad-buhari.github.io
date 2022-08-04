---
title: Ruby Basics
author: Ahmad Buhari
date: 2022-08-04 14:10:00 +0800
categories: [tutorials,ruby]
tags: [ruby]
render_with_liquid: false
---

A quick guide for ruby syntax. 

## Strings

### String Interpolation in ruby
Use the synatx `#{}`

```
first_name = Joe
age = 26
puts "Your name is #{first_name} and you are #{age} years old"
```
<br>

### Commenting
Use the # sign, example `# This is a comment`

<br>

### Grabing user input
Use the `get.chomp` statemement
```
puts "What is your name?"
name = gets.chomp
puts "Hello, #{name}!"  
```