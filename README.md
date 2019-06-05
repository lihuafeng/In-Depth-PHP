# In-Depth-PHP
PHP深度学习

#### 命令行脚本接收传入参数的三种方式

php一般都做http方式请求了，可以使用get或post接收参数。当php做为脚本执行时，例如定时任务，就可能要接收传入参数

1. 使用$argc和$argv接收
```
echo "接收到{$argc}个参数";
print_r($argv);
echo "\n";

edzdeMacBook-Air-4:html edz$ php test.php 222  333 444
接收到4个参数Array
(
    [0] => test.php
    [1] => 222
    [2] => 333
    [3] => 444
)

```

2. 使用getopt函数

```
$param_arr = getopt('a:b:');
print_r($param_arr);
echo "\n";

edzdeMacBook-Air-4:html edz$ php test.php -a 345
Array
(
    [a] => 345
)

edzdeMacBook-Air-4:html edz$ php test.php -a 345 -b 12
Array
(
    [a] => 345
    [b] => 12
)


```

3. 提示用户输入

```
$fs = true;
do{
        if($fs){
                fwrite(STDOUT,"请输入姓名:");
                $fs = false;
        }else{
                fwrite(STDOUT,"抱歉，姓名不能为空！请重新输入:");
        }
        $name = trim(fgets(STDOUT));
}while(!$name);
echo "输入的姓名是:".$name."\r\n";

edzdeMacBook-Air-4:html edz$ php test.php 
请输入姓名:测试
输入的姓名是:测试
edzdeMacBook-Air-4:html edz$ php test.php 
请输入姓名:
抱歉，姓名不能为空！请重新输入:

```
