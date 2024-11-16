```python
import numpy as np
from typing import Union

def linear_regression(x: Union[np.ndarray, list], y: Union[np.ndarray, list]) -> tuple[float, float]:
    """
    Обчислює коефіцієнти лінійної регресії (нахил m та перетин b) для рівняння y = m * x + b.
    Параметри:
        x (array-like): Вхідні дані для незалежної змінної.
        y (array-like): Вхідні дані для залежної змінної.
    Повертає:
        m (float): Нахил регресійної лінії.
        b (float): Перетин регресійної лінії.
    """
    # Обчислюємо середні значення
    mean_x = np.mean(x)
    mean_y = np.mean(y)
    mean_xy = np.mean(x * y)
    mean_x2 = np.mean(x ** 2)

    # Обчислюємо коефіцієнти лінійної регресії
    m = (mean_x * mean_y - mean_xy) / (mean_x ** 2 - mean_x2)
    b = mean_y - m * mean_x
    print(f"y={m}*x+({b})")
    return m, b
```
