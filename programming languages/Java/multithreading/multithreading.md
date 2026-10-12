Differences:
1. if you extend the thread class, you can't extend other classes. Extension is possible if you implement the runnable interface
2. Thread class provides inbuilt methods like yield and interrupt that aren't available in the Runnable interface
3. Runnable will give an object that can be shared among multiple threads