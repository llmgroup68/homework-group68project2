# homework-group68project2
Project2: implement the Rho method of reduced SM3


实现方式：Python

成员：李丽敏 202100460130（仅一人一组）

实验概述：（仅展示部分关键代码）

首先写了一些关于SM3的函数定义：

![image](https://github.com/llmgroup68/homework-group68project2/assets/138642474/43a1bbf1-cc29-417a-b186-c21d2b995300)

其次写了一些辅助函数：

1：在 Fill() 函数中，对原始消息进行填充，确保满足 SM3 哈希算法的长度要求。


![image](https://github.com/llmgroup68/homework-group68project2/assets/138642474/595acd87-83e4-409b-97fc-61e5e0d3af33)

2：使用 Group() 函数将填充后的消息分组。

![image](https://github.com/llmgroup68/homework-group68project2/assets/138642474/bbb10725-bfb0-4d17-8e0b-bf696aa7d5e0)



3：在 Expand() 函数中，根据当前块的索引号 n，从分组消息中获取 W 和 W' 数组，并按照一定规则对其进行计算和转换。

![image](https://github.com/llmgroup68/homework-group68project2/assets/138642474/5b138dcb-f625-4ac8-b378-71f6618b996f)



4：在 CF() 函数中，根据 W 和 W' 数组，以及一系列变量和常量，实现 SM3 的压缩函数。

![image](https://github.com/llmgroup68/homework-group68project2/assets/138642474/bd425af5-b4cb-4288-a1ea-40866b630a77)



5：Iterate() 函数使用 CF 函数进行迭代计算，返回最终的结果。

![image](https://github.com/llmgroup68/homework-group68project2/assets/138642474/b9d861f8-b842-4fa8-8a14-ecae8c51a146)


Rho 方法的实现：

rho_method() 函数实现了 rho 方法，用于寻找哈希碰撞。在函数中，生成一个随机数并计算其 SM3 哈希值，然后通过迭代计算两个变量 x_a 和 x_b，直到它们的指定比特位相同。最后，通过比较 x_a 的哈希值和 x_b 的哈希值来寻找哈希碰撞。


示例代码：

![image](https://github.com/llmgroup68/homework-group68project2/assets/138642474/baa82365-d44c-4f3b-99e1-660802ef4c3e)


最后，在 if __name__ == '__main__': 条件下，演示了如何使用脚本计算消息 '616263' 的 SM3 哈希值，并展示了 rho 方法寻找哈希碰撞的结果。
通过调用 SM3('616263') 可以获取消息 '616263' 的 SM3 哈希值。
使用 rho_method(example) 函数可以进行 rho 方法的演示，其中 example 可以指定前几个比特位相同。


结果展示：

![image](https://github.com/llmgroup68/homework-group68project2/assets/138642474/d51b859e-bced-4f8a-9747-67a69bfd1955)

实验补充：rho原理：

Rho 方法是一种寻找哈希碰撞的方法，即在哈希函数中找到两个不同的输入消息，但它们的哈希值在指定比特位上相同。


这个方法基于迭代计算，在每次迭代中使用不同的输入消息来计算哈希值。


通过比较两个消息的哈希值的指定比特位，当它们相同时，表示找到了一个哈希碰撞。


在这个实验中，我们使用 SM3 哈希算法和 rho 方法来演示寻找哈希碰撞的原理。

  首先，我们使用函数 SM3() 计算了消息 '616263' 的 SM3 哈希值，得到一个哈希结果。

  然后，我们使用函数 rho_method() 来进行 rho 方法的实验。

       ①在实验中，我们生成一个随机数，并计算它的 SM3 哈希值作为起始点。

       
       ②通过迭代计算，我们不断调整输入消息，并计算每个消息的哈希值。

       
       ③当找到两个消息的指定比特位相同时，我们停止迭代，表示找到了一个哈希碰撞。
