1. visualization
- show()
- plot()
![unnamed_84b2a03f25f9490799a57223e0f525d5](unnamed_84b2a03f25f9490799a57223e0f525d5.png)
- scatter()
![unnamed_a25f6664beb74c3ab1b8de547fd40409](unnamed_a25f6664beb74c3ab1b8de547fd40409.png)
- bar()/barh()
![unnamed_f66591395b504009b4ce87c803cba3c7](unnamed_f66591395b504009b4ce87c803cba3c7.png)
- hist()
![unnamed_a1ecfffdbaf54749aa562c4dae3cb938](unnamed_a1ecfffdbaf54749aa562c4dae3cb938.png)
- subplots()

![unnamed_31ff9d17ee124735a47662edaa596a3a](unnamed_31ff9d17ee124735a47662edaa596a3a.png)![unnamed_ab1301bd21db48c7b4b9cf7248120e6c](unnamed_ab1301bd21db48c7b4b9cf7248120e6c.png)
- figure()

```python3
fig = plt.figure()
ax1 = fig.add_subplot(221)
ax2 = fig.add_subplot(2, 2, 2)
ax3 = fig.add_subplot(223)
ax4 = fig.add_subplot(224)
ax1.hist(arr1)
ax2.plot(arr2)
ax3.bar(arr3)
ax4.plot(arr4)
ax1.title.set_text('First Plot')
ax2.title.set_text('Second Plot')
ax3.title.set_text('Third Plot')
ax4.title.set_text('Fourth Plot')
plt.show()
```


2. labels
- title()
- xlabel()
- ylabel()

reference:
- 가천대 - Python programming