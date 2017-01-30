# External module for Artificial Artist environment class.

## Import with:
```python
from aa_enviroment import *
```


## Instantiating Environment class
```python
env = Environment( fp )
```
#### Parameters:
**fp** (_String, optional_) File path for source image
#### Returns:
**Environment** (_object_)

## Reset Environment
```python
env.reset( fp )
```
_Runs all setup functions to load new source image, resize, and initialize canvas and "brush" position and stroke opacity._
#### Parameters:
**fp** (_String_) File path for source image
#### Returns:
**None**


## Adjust Stroke Opacity
```python
env.setBrushOpacity( opacity )
```
_Alters the opacity of simulated paint from 0.0 (100% transparent) to 1.0 (100% opaque)._
#### Parameters:
**opacity** (_Float, optional_) % Opacity for simulated strokes. Default value = 0.25:
#### Returns:
**None**

## Set Reward Blur Level
```python
env.setRewardBlur( level )
```
_Set blurring intensity - lower values equal less blurring, and higher values equal more blurring._
#### Parameters:
**level** (_Float, optional_) Standard deviation for Gaussian kernel. Default value = 1.0:
#### Returns:
**None**



## Display Current State (Visual)
```python
env.showSource() #displays source image
env.showCanvas() #display canvas
env.showBrush() #display brush position

env.showAll() #display source, canvas, and brush position
```
_Plots the layers of the environments states. Individual commands display elements separately, and_ `.showAll()` _displays all three. The_ `.showBrush()` _command also reports back (x,y) position of brush._
#### Parameters:
**None**
#### Returns:
**None**

## Update State
```python
env.update( action )
```
_Executes an input action._
#### Parameters:
**action** (_Tuple_) Expects (x, y, b) format where:
+ **x** (_int_) : movement in x-axis relative to current position
+ **y** (_int_) : movement in y-axis relative to current position
+ **b** (_bool, 0 or 1_) : paint deposit toggle

#### Returns:
**None**

## Get Current State (Values)
```python
env.getState()
```
_Returns combined state elements as numpy stack._
#### Parameters:
**None**
#### Returns:
**state** (_ndarray, (H,W,3)_) NumPy array stack of source, canvas, and brush position.

## Get Reward
```python
env.getReward()
```
_Returns a scalar value representing the mean absolute difference between the source image and the canvas after a blurring filter has been applied to each. Blur intesity can be varied using_ `.setRewardBlur()`
#### Parameters:
**None**
#### Returns:
**reward** (_float_) Mean distance between blurred source image and blurred canvas.

## Get Combined State & Reward
```python
env.getUpdate( action )
```
_Returns current state and reward. See_ `.getState()` _and_ `.getReward()` _for individual method details._
#### Parameters:
**action** (_Tuple_) Expects (x, y, b) format where:
+ **x** (_int_) : movement in x-axis relative to current position
+ **y** (_int_) : movement in y-axis relative to current position
+ **b** (_bool, 0 or 1_) : paint deposit toggle

#### Returns:
**State/Reward** (_array, [ndarray, float]_) Bundled state numpy array stack and reward scalar.
