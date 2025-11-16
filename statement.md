# Root of Digital Root

For a given number `N` calculate iteratively the **Digital Root** until the result has only 1 digit (is in range 0..9).

The Digital Root is calculated by summing up all digits of a number. 
E.g. {{2025}} has a Digital Root of {{9}} because `2+0+2+5 = 9`

If the digital root is higher than 9, continue calculate the digital root of the result.

```python runnable
def root_of_digital_root(n:int):
    # TODO: add your calculation here
    result = n
    return n


INPUT = [2025, 0, 9999, 17112025]
EXPECTED_OUTPUT = [9, 0, 9, 1]
for N, expected in zip(INPUT, EXPECTED_OUTPUT):
    result = root_of_digital_root(N)
    if result == expected:
        print(f'Root of Digital Root for {N} is {result}')
    else 
        print(f'ERROR: Root of Digital Root for {N} is {result}, but expected was {expected}')
        break
```

