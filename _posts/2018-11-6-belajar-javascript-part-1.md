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
>Basically, when we evaluate the performance of our JS code, so a function in a stack makes it slow or fast, console.log() will be fast but performing iteration with for or while over thousands or millions of line items will be slower, and will keep the stack occupied or blocked. This is termed as blocking script, which you have read or heard about in Webpage Speed Insights.
Network requests can be slow, the image requests can be slow, but thankfully the server requests can be done through AJAX, an asynchronous function. If suppose, these network requests are made through synchronous functions, then what would happen? The network requests are send to some server, which is basically another computer/machine somewhere. Now, computers can be slow sending back the response. In the meantime , if I click some CTA button, or some other rendering needs to be done, nothing will happen as the stack is blocked. In multi threaded language like Ruby, it can be handled, but in single threaded language like Javascript, this is not possible unless function inside the stack returns a value. The webpage will hell breaks loose as the browser can’t do anything. This is not ideal if we want fluid UI for the end user. How do we handle this?

# Monkey Patch
A monkey patch is a way for a program to extend or modify supporting system software locally (affecting only the running instance of the program).
