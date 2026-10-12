
```python3
from dataclasses import dataclass

@dataclass
class PhysicsResult:
	velocity: float
	mass: float
	force: float
	# ... add all 15 fields here

def run_simulation() -> PhysicsResult:
	return PhysicsResult(velocity=10.5, mass=2.0, force=21.0, ...)
```


- subclassing

```python3
from dataclasses import dataclass

@dataclass
class X:
    name: str
    size: int

@dataclass
class Y(X):
    extra_feature: str

# Usage: Provide parent fields first, then child fields
subset = Y(name="Widget", size=10, extra_feature="Turbo")
print(subset) 
# Output: Y(name='Widget', size=10, extra_feature='Turbo')
```
