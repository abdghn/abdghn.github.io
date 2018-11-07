---
title: Belajar Javascript Part 1
description: Mempelajari tentang javascript pada function executions yaitu Call Stack,Event Loop, Tasks dll
---
#Function Executions
Kebanyakan pembuatan app menggunakan Javascript dibangun dengan V8, yaitu runtime yang dimiliki oleh chrome. untuk pemahaman lebih lanjut dapat ditonton video yang dijelaskan oleh Philip Robert,
[What the heck is the event loop anyway?](https://www.youtube.com/watch?v=8aGhZQkoFbQ)
## Call Stack
>It’s a data structure which records the function calls, basically where in the program we are. If we call a function to execute , we push something on to the stack, and when we return from a function, we pop off the top of the stack.



sebelum memulai call stack memahami terlebih dahulu tentang Execution Context.
### Execution Context

Call Stack merupakan pemanggilan fungsi - fungsi menggunakan konsep Stack. Stack merupakan sturktur data dimana data dipanggil dengan Last In First Out(LIFO) ketika fungsi pada javascript paling belakang, maka akan tercetak

## Heap
>Objects are allocated in a heap i.e mostly unstructured region of memory. All the memory allocation to variables and objects happens here.

## Queue
>A JavaScript runtime contains a message queue, which is a list of messages to be processed and the associated callback functions to execute. When the stack has enough capacity, a message is taken out of the queue and processed which consists of calling the associated function (and thus creating an initial stack frame). The message processing ends when the stack becomes empty again. In basic words , these messages are queued in response to external async events(such as a mouse being clicked or receiving the response to an HTTP request), given a callback function has been provided. If, for example a user were to click a button and no callback function was provided — no message would have been enqueued.

## Event Loop

# Monkey Patch
A monkey patch is a way for a program to extend or modify supporting system software locally (affecting only the running instance of the program).
