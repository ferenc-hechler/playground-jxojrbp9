# Digital Root

For a given number `N` calculate the **Digital Root**.

The Digital Root is calculated by summing up all digits of a number. 
E.g. `2025` has a Digital Root of `9` because `2+0+2+5 = 9`

Implement the method solution(input) and start the code to run the testscases. 

```python runnable
def solution(input:int):

    # ---------------------------- #
    # - TODO: ADD YOUR CODE HERE - #
    # ---------------------------- #
    num_string = str(input)
    result = 0
    for digit in num_string:
        result = result + int(digit)

    return result


# -------------------------------------------------- #
# ---------- DO NOT MODIFY THE CODE BELOW ---------- #
# -------------------------------------------------- #

INPUTS = [2025, 0, 9999, 17112025]
CHECKS = [3205138698, 3158815156, 3540719418, 3071405752]

import sys
import hashlib
from datetime import datetime, timedelta

for N, check in zip(INPUTS, CHECKS):
    result = solution(N)
    chk = hashlib.md5(f"{N}{result}".encode()).digest()
    chk = (((chk[3]<<8)+chk[2]<<8)+chk[1]<<8)+chk[0]
    #print(chk)
    if chk == check:
        print(f'GOOD: Digital Root for {N} is {result}')
    else:
        print(f'FAIL: Digital Root for {N} is not {result}', file=sys.stderr)
        sys.exit(1)
        
print("------------------------------------------------------------")
print(f"SUCCESS: congratulations, you solved the riddle at {datetime.now()+ timedelta(hours=1)}")

```

