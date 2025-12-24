# Matplotlib Cheat Sheet

## Table of Contents

- [Installation](#installation)
- [Basic Plotting](#basic-plotting)
- [The Figure and Axes](#the-figure-and-axes)
- [Customizing Plots](#customizing-plots)
- [Common Plot Types](#common-plot-types)
- [Working with Multiple Plots](#working-with-multiple-plots)
- [Adding Text and Annotations](#adding-text-and-annotations)
- [Saving Plots](#saving-plots)
- [References](#references)

## Installation

```bash
pip install matplotlib
```

```python
import matplotlib.pyplot as plt
%matplotlib inline
# When using 'inline' backend, your matplotlib graphs will
# be included in your notebook, next to the code.
```

```python
import warnings
warnings.filterwarnings('ignore')
```

## Basic Plotting

The quickest way to create a plot. Useful for simple, fast visualizations.

```python
# Sample Data
x = np.linspace(0, 10, 100)
y = np.sin(x)

# A simple line plot
plt.plot(x, y)
plt.title("Simple Sine Wave")
plt.xlabel("x-axis")
plt.ylabel("y-axis")
plt.show()
```

## The Figure and Axes

For more control and creating complex plots, use the object-oriented approach. This is the recommended best practice.

- Figure: The overall window or page that everything is drawn on.
- Axes: The actual plot or chart. A figure can have multiple axes.

```python
# Create a figure and a set of subplots (in this case, just one)
fig, ax = plt.subplots()

# Plot data on the axes
ax.plot(x, y)

# Set labels and title on the axes
ax.set_title("Sine Wave using OO Approach")
ax.set_xlabel("x-axis")
ax.set_ylabel("y-axis")

# Display the plot
plt.show()
```

## Customizing Plots

Modify the appearance of your plots using various parameters.

```python
fig, ax = plt.subplots()

x2 = np.linspace(0, 10, 100)
y2 = np.cos(x2)

ax.plot(x, y,
        color='blue',          # Line color
        linestyle='--',       # Line style: '-', '--', ':', '-.'
        linewidth=2,           # Line width
        marker='o',            # Marker style: 'o', 's', '^'
        markersize=4,          # Marker size
        label='Sine')          # Label for the legend

ax.plot(x2, y2, color='red', label='Cosine')

ax.set_title("Customized Plot")
ax.set_xlabel("Angle [rad]")
ax.set_ylabel("Value")

ax.grid(True)     # Add a grid
ax.legend()       # Add a legend
plt.show()
```

## Common Plot Types

Create different types of plots using ax methods.

```python
# Create a 2x2 grid of plots
fig, axs = plt.subplots(2, 2, figsize=(10, 8))

# --- Scatter Plot ---
x_rand = np.random.rand(50)
y_rand = np.random.rand(50)
axs[0, 0].scatter(x_rand, y_rand)
axs[0, 0].set_title('Scatter Plot')

# --- Bar Chart ---
categories = ['A', 'B', 'C']
values = [10, 20, 15]
axs[0, 1].bar(categories, values)
axs[0, 1].set_title('Bar Chart')

# --- Histogram ---
data = np.random.randn(1000)
axs[1, 0].hist(data, bins=30)
axs[1, 0].set_title('Histogram')

# --- Box Plot ---
data_for_boxplot = [
    np.random.normal(0, std, 100) for std in range(1, 4)
    ]
axs[1, 1].boxplot(data_for_boxplot)
axs[1, 1].set_title('Box Plot')

plt.tight_layout() # Adjust layout to prevent overlap
plt.show()
```

## Working with Multiple Plots

The subplots function is the easiest way to create a grid of plots.

```python
# Create a figure with two subplots, sharing the x-axis
fig, (ax1, ax2) = plt.subplots(2, 1, sharex=True)

ax1.plot(x, y, color='blue')
ax1.set_title('Sine and Cosine Waves')
ax1.set_ylabel('Sine')
ax1.grid(True)

ax2.plot(x, np.cos(x), color='red')
ax2.set_ylabel('Cosine')
ax2.grid(True)

plt.show()
```

## Adding Text and Annotations

Add text or arrows to highlight specific points.

```python
fig, ax = plt.subplots()
ax.plot(x, y)

# Add simple text
ax.text(2, 0, 'Some text', fontsize=12)

# Add an annotation with an arrow
ax.annotate('Peak', xy=(np.pi/2, 1),
            xytext=(3, 1.5),
            arrowprops=dict(facecolor='black', shrink=0.05))

ax.set_ylim(-2, 2) # Adjust y-limits to make space for text
plt.show()
```

## Saving Plots

Save your figure to a file. Matplotlib supports many formats like PNG, PDF, SVG, etc.

```python
fig, ax = plt.subplots()
ax.plot(x, y)
ax.set_title("My Saved Plot")

# Save the figure to a file
# Use a high DPI (dots per inch) for better quality
fig.savefig('sine_wave.png', dpi=300)
```

## References

- Matplotlib Official Documentation
- Matplotlib Pyplot API
- Matplotlib Examples Gallery
