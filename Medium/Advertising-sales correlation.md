---
difficulty: Medium
---
Plot a bubble chart to explore the correlation between advertising spend and sales volume across different media channels, using 'chocolate' for TV, 'cyan' for online, and 'crimson' for print media.

### Matplotlib Color Mapping

colors = {'TV': 'chocolate', 'Online': 'cyan', 'Print': 'crimson'}

### Matplotlib Figure Size

figsize=(10, 6)

### Plotly Color Mapping

color_discrete_map={'TV': 'chocolate', 'Online': 'cyan', 'Print': 'crimson'}

| media_channel | ad_spend | sales_volume |
| ------------- | -------- | ------------ |
| TV            | 71615    | 684          |
| Online        | 68564    | 445          |
| Print         | 59689    | 466          |
| TV            | 20742    | 654          |
| Online        | 63459    | 830          |
| Print         | 76455    | 267          |
| TV            | 89463    | 168          |
| Online        | 66718    | 532          |
| Print         | 78119    | 995          |
ad_spend:int64
sales_volume:int64
media_channel:object

Here's a Python code snippet to create a bubble chart showing the correlation between advertising spend and sales volume across different media channels (TV, Online, Print) with the specified colors:

```python
import matplotlib.pyplot as plt
import pandas as pd

# Data
data = {
    'media_channel': ['TV', 'Online', 'Print', 'TV', 'Online', 'Print', 'TV', 'Online', 'Print'],
    'ad_spend': [71615, 68564, 59689, 20742, 63459, 76455, 89463, 66718, 78119],
    'sales_volume': [684, 445, 466, 654, 830, 267, 168, 532, 995]
}

df = pd.DataFrame(data)

# Color mapping
colors = {'TV': 'chocolate', 'Online': 'cyan', 'Print': 'crimson'}

# Create figure
plt.figure(figsize=(10, 6))

# Plot each media channel separately
for channel in df['media_channel'].unique():
    subset = df[df['media_channel'] == channel]
    plt.scatter(
        x=subset['ad_spend'], 
        y=subset['sales_volume'],
        s=subset['sales_volume']*2,  # Bubble size based on sales volume
        c=colors[channel],
        label=channel,
        alpha=0.6,
        edgecolors='w'
    )

# Add labels and title
plt.xlabel('Advertising Spend ($)')
plt.ylabel('Sales Volume')
plt.title('Correlation Between Advertising Spend and Sales Volume by Media Channel')
plt.grid(True, alpha=0.3)

# Add legend
plt.legend(title='Media Channel')

# Show plot
plt.tight_layout()
plt.show()
```

This code will:
1. Create a bubble chart with advertising spend on the x-axis and sales volume on the y-axis
2. Use different colors for each media channel (chocolate for TV, cyan for Online, crimson for Print)
3. Make the bubble sizes proportional to sales volume
4. Include a legend and proper labels
5. Use the specified figure size of 10x6 inches

The bubble sizes are scaled to be twice the sales volume value to make them visibly distinct while maintaining proportionality. The alpha value is set to 0.6 to allow for some transparency when bubbles overlap.