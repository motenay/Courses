# Concurrency in C#: Practicum

This document class activities and exercises are described to be practised in practicums of Concurrency course of Hogeschool Rotterdam.

### Practical notes:
1. The exercises of each week coresponds to some of the source codes available here in Github: https://github.com/afshinamighi/Courses
2. Coresponding C# projects are represented with bold font at each exercise.
3. In each exercise, students are expected to evaluate specified source codes, understand the structures, analyze expected behaviours of the programs (guess and justify the output), and in some cases reproduce the concept in a different context.
4. In some of the exercises, students are asked to share / discuss / explain results of their evaluations. The teacher will determine how results will be shared with other students and/or the teacher.
5. This document will be updated weekly. 



# Week 1: 
Main objectives of this week is to introduce the main concepts and prepare practical tools needed for upcoming weeks.

## Preparation:
1.	 We will discuss about threads in week 3. Here, just think about a thread as a separate paths of execution that can be executed simultanously with the main program.
2.	 Refresh your C# programming environment: You are expected to be able to write simple console based programs. A set of possible concepts to be used later are: fundamentals (types, conditional statements, loops), defining attributes, methods, public / private / static, arrays, anonymous functions.
3.	Implement a simple program: like a counter class that counts until a given number and the main program instantiates an object from this class and prints the final result. The counter class has a state that keeps the latest counting value.


## Exercises:
1. Concurrency in your machine:
	1.	[~ 10 min ] Make a list of parallel/concurrent programs in your computer: (recall that in mac the command [ps -ax] makes a list of currently running processes with PID and the location of the executable programs). Choose a running program (for example PyCharm) and see how many threads are running by the application.
	2.	[~ 10 min ] Open an internet browser with several tabs. Check how many threads are created. Make a list (at least five) of functionalities (tasks) that each thread of execution is responsible to execute. Share your list with the teacher.
2. [~ 20 min ] **SocketClient, SocketServer**: 
	1.	These two projects implement a simple client and server programs in C#. Create a project in your local machine and run both client and server. Check how network communication is working in this simulation. 
	2.	Assume you are asked to simulate multiple clients trying to communicate with the server simultaneously. How would you do that? What would you need? Explain the logic through the provided client code. Is current server implementation able to handle multiple simultaneous clients? If not, what would be your proposal to solve it? Explain the logic through the provided server code.
3. [~ 30 min ] **MergeSort**: One of the challenges in designing a concurrent program is to recognise potential concurrent tasks. 
	1.	Among various sort algorithms one of the well-known ones is named **merge sort** algorithm. Read and understand how this algorithm works. You can use the following sesources: [check here](https://www.hackerearth.com/practice/algorithms/sorting/merge-sort/visualize/) , or [here, just don't forget to choose right settings](https://visualgo.net/bn/sorting?slide=1).
	2. Can you recognise sorting tasks that can be done simultaneously? Share your answer with the teacher. **Note**: In week three you will be asked to implement a concurrent version of this algorithm. Therefore, this exercise is crucial to understand and share your ideas. In Week 1, ignore the class named **ConcurrentMergeSort** and its todos.





# Week 2:

The main objectives are to understand and apply concepts of processes and inter-process communications in programming. In this week you will learn:
- how to obtain processes information from os.
- how to create and run a process through a program.
- how can two running processes communicate with each other.

## Preparation:
1. Use the online reference below and answer the questions:
Reference: [Process handling in C#](https://www.dotnetperls.com/process)
- Which namespace is needed?
- Which class and method are used to run a process?
- How can we modify properties of a process?
- How can we get a list of currently running processes?
2. Use the online reference below to find more information about **Process** component.
Reference: [System calls to make processes](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.process?view=netframework-4.8) 

## Exercises:

1. [~ 20 min ] **Processes**: The program will give a list of currently running processes. Names and Ids are printed. 
	1. Compare Ids and Names with your machine activity (task) manager program. Choose a process id from your computer that its termination is safe: like whatsapp, editors, browser. Check if the program terminates the given process completely.
	2. Add a method to the program that gets the name of a process and prints the related id.
2. [~ 20 min ] **ProcessCreation**: Implement a program, that executes a command, like **ls**. Modify your program such that executes the result of **Processes** (previous exercise).

3. [~ 30 min ] **IPCNamedClient, IPCNamedServer**: Two projects are implemented to present how two programs can communicate using named pipes.
**Note**: Client and server naming is not following strict definition of client-server roles, it is just oriented to have a peer to peer communication.
	1. Read and analyse the programs for both client and server. What do you expect from the behaviour of these programs?
	2. Run the server, run the client. Check the behaviour.
	3. Run one server and two clients. Does the server communicate with both clients?
	4. What will happen if the name of the pipe in the server is different from the client? Change the name of the pipe in the server (or the client). Re-run both the client and server. Can they communicate? 
	5. Named pipes are meant for programs where two-way communication is needed. The current implementation provides only one-way communication (from the server to the client). Extend the programs such that the client sends the result of its processing (i.e. reversed message) back to the server. The server will print the result received from the client.
<!-- Solution: Is available. -->

4.  [~ 20 min ] Using named pipes implement a client / server program that the client sends the name and the path of an executable program to the server and the server starts the process given by the client.

<!-- (Optional) Read this tutorial and practice an example about AnonymousPipes: https://ingeno.io/2016/09/c-anonymous-pipes-for-interprocess-communication/  -->



## Assignment: Practical steps
Description of the assignment and deliveries will be published by the teacher. Here we try to provide some steps that practically can lead students to implement a solution for the assignment. **Note**: These steps will be updated regularly during the course period.

During the course after Week ...
1. students can download and execute coresponding projects. They should spend enough time to understand details of the code and provided structure, modify and extend the code.
2. students can make a list of commands in the client side. They should modify server such that it can execute the command sent by the client.
3. students can extend client side such that it simulates a number of concurrent clients all trying to simultaneously communicating with the server.
4. students can extend the server that can handle multiple simultaneous clients.
5. students can extend the server with a proper shared structure such that stores received data from all the clients.
6. students can extend the server with a solution to make the server thread safe, i.e no data race.
7. students can execute and test their final results: ~ 500 simultenous clients.
Then, the solution is ready. Students should apply all the requested formats and deliver their solutions according given instructions.
