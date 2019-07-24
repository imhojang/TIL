Javascript is a single threaded programming language, which means that it can only handle one task at a time.  
It will not execute the next line of code unless it is finished with current execution. It could be said that the
current execution is "blocking" the next execution. The way Javascript behaves could also be described as synchronous.
However, synchronous manner of taking care of things doesn't seem so efficient when there are executions that take long time.  

So, how does Javascript handle this issue? In case we want to move on with other pending executions, Javascript can behave in
a different manner, which handles executions asynchronously. When executions are handled asynchronously, it sends request to handle
it on a separate thread outside of Javascript (ex. the browser). The pending executions are carried on without delay in synchronous manner.
Then when the data is retrieved, it is added to the end of the callback queue.

There are a few asynchronous control flows: callback (good), promise (better), generators (awesome).
