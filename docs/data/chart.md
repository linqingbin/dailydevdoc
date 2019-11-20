# Chart
Scatter Chart
```python
tops = report1[:100]
xlabel = "xLabel"
ylabel = "yLabel"

x = tops[xlabel]
y = tops[ylabel]
s = tops['index']
texts = tops.index
fig, ax = plt.subplots(figsize=(40,20))
ax.scatter(x,y,s=s)
plt.xlabel(xlabel)
plt.ylabel(ylabel)

exists = []
for i, txt in enumerate(texts):
    loc = (x[i], y[i])
    ax.annotate(txt, loc)
    exists.append(loc)
```

Display utf-8 character in matplorlib chart
```python
from matplotlib.font_manager import FontProperties
from matplotlib import pyplot as plt
font = FontProperties(fname= "c:/windows/fonts/simsun.ttc", size=14)
plt.title("百分位图", fontproperties = font)
plt.xticks(fontproperties=font)
```
Display utf-8 character in Graphviz chart

    1. Set fonts.conf in Graphviz.
    2. Change souce format as gbk in python graphviz.
    3. Add `node[fontname = "PMingLiu"];` in dot file.