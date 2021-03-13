### 效果图：

![image.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/eb0f51af80aa4e6d81b818846358e5b0~tplv-k3u1fbpfcp-watermark.image)

**上菜：**

### **1、RadarChartRenderer中drawWeb(Canvas c)内设置如下大菜：**


```js
    protected Path mDrawWebBg = new Path();
    protected void drawWeb(Canvas c) {
        Path surface = mDrawWebBg;
        surface.reset();
        boolean hasMovedToPoint = false;

        for (int i = 0; i < maxEntryCount; i += xIncrements) {

            if (mChart.isWebBackgroundOpen()) {
                //绘制背景的路径
                if (!hasMovedToPoint) {
                    surface.moveTo(p.x, p.y);
                    hasMovedToPoint = true;
                } else {
                    surface.lineTo(p.x, p.y);
                }
            }

        }
        if (mChart.isWebBackgroundOpen()) {
            //填充背景
            drawFilledPath(c, surface, mChart.getWebBackgroundColor(), mChart.getWebBackgroundFillAlpha());
        }
        surface.close();
```

### **2、RadarChart中叫上服务员：** 



```js
    /**
     * 蛛网背景色默认关闭设置
     */
    private boolean mWebBackgroundOpen = false;
    /**
     * 蛛网背景色，默认
     */
    private int mWebBackgroundColor = -1;
    /**
     * 不透明度 (0-255)
     */
    private int mWebBackgroundFillAlpha = 180;
    
    /**
     * 设置蛛网背景色与透明度
     *
     * @param color
     * @param fillAlpha
     */
    public void setWebBackgroundColor(boolean isOpen, int color, int fillAlpha) {
        this.mWebBackgroundOpen = isOpen;
        this.mWebBackgroundColor = color;
        this.mWebBackgroundFillAlpha = fillAlpha;
    }

    public int getWebBackgroundColor() {
        return mWebBackgroundColor;
    }

    public int getWebBackgroundFillAlpha() {
        return mWebBackgroundFillAlpha;
    }

    public boolean isWebBackgroundOpen() {
        return mWebBackgroundOpen;
    }
```

### 3、该你喊服务员了：

```js
        chart.setWebBackgroundColor(true, Color.rgb(255, 189, 0), 180);
```

### 餐厅地址：
https://github.com/hzl512/MPAndroidChartRendererBg.git

换行参考：https://github.com/NanBox/MPAndroidChart-Newline.git

喜欢就给个star呗~
