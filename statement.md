# Digital Root

For a given number `N` calculate iteratively the **Digital Root**.
The Digital Root is calculated by summing up all digits of a number. 
E.g. {{2025}} has a Digital Root of {{9}} because `2+0+2+5=9`


```python runnable
def digital_root(n:int) {
    """TODO: add your calculation here"""
    result = n
    return n
}

INPUT = [2025, 0, 9999, 17112025]
for N in INPUT:
    print(f'Digital Root of {N} is {digital_root(N)}')
```

