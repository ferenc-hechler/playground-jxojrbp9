# Root of Digital Root

For a given number `N` calculate iteratively the **Digital Root** until the result has only 1 digit (is in range 0..9).

The Digital Root is calculated by summing up all digits of a number. 
E.g. {{2025}} has a Digital Root of {{9}} because `2+0+2+5 = 9`

If the digital root is higher than 9, continue calculate the digital root of the result.

```python runnable
def digital_root(n:int):

    # ---------------------------- #
    # - TODO: ADD YOUR CODE HERE - #
    # ---------------------------- #
    result = n

    return result


# -------------------------------------------------- #
# ---------- DO NOT MODIFY THE CODE BELOW ---------- #
# -------------------------------------------------- #

import hashlib
INPUT = [2025, 0, 9999, 17112025]
CHECKS = [3205138698, 3158815156, 3540719418, 3071405752]
success = True
for N, check in zip(INPUT, CHECKS):
    result = root_of_digital_root(N)
    chk = hashlib.md5(f"{N}{result}".encode()).digest()
    chk = (((chk[3]<<8)+chk[2]<<8)+chk[1]<<8)+chk[0]
    print(chk)
    if chk == check:
        print(f'GOOD: Digital Root for {N} is {result}')
    else:
        print(f'FAIL: Digital Root for {N} is not {result}')
        success = False
        break
if success:
    from datetime import datetime, timedelta
    print(f"SUCCESS: congratulations, you solved the riddle at {datetime.now()+ timedelta(hours=1)}")
```

