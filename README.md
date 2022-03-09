# POS in Shell

The demo shows a simple POS system with command line interface. 

To run

```shell
mvn clean spring-boot:run
```

Currently, it implements three commands which you can see using the `help` command.

```shell
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::                (v2.5.7)
 
shell:>help
AVAILABLE COMMANDS

Built-In Commands
        clear: Clear the shell screen.
        exit, quit: Exit the shell.
        help: Display help about available commands.
        history: Display or save the history of previously run commands
        script: Read and execute commands from a file.
        stacktrace: Display the full stacktrace of the last error.

Pos Command
        a: Add a Product to Cart
        n: New Cart
        p: List Products
```

Everytime a customer come to make a purchase, use `n` to create a new cart and then use `a ${productid} ${amount}` to add a product to the cart.

Please make the POS system robust and fully functional by implementing more commands, for instance, print/empty/modify cart.

Implementing a PosDB with real database is very much welcome. 

Please use asciinema (https://asciinema.org) to record a demo and submit the url in QQ group. 

And please elaborate your understanding in layered systems via this homework in your README.md.

## 个人对分层结构的理解

以本项目为例：

1. cli：定义shell层的命令，即与用户进行交互，将命令的具体实现交给PosService来完成；

2. biz：定义PosService，负责命令的具体实现，对数据的处理交给database来完成；

3. db：负责数据的处理，但对于数据对象的实现方式并不关心，只调用接口来进行操作；

4. model：负责数据对象的具体实现，同时向上提供统一的调用接口；

