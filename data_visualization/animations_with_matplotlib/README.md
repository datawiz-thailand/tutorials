# Animation with Matplotlib

## Live graph

![](docs/live_graph.gif)


```python
import matplotlib.pyplot as plt
import matplotlib.animation as animation
import pandas as pd

fig = plt.figure()
ax = fig.add_subplot(1,1,1)

def live_update(i):

    # load data
    df = pd.DataFrame.from_csv('live_graph_stock.csv', index_col=None)

    xs = df['Date'].values
    ys = df['Price'].values

    # visualize
    ax.clear()
    ax.plot(xs, ys)

    plt.xlabel('Date')
    plt.ylabel('Price')
    plt.title('Live Stock Chart with Matplotlib')

# interval -> Delay between frames in milliseconds
ani = animation.FuncAnimation(fig, live_update, interval=500)
plt.show()
```