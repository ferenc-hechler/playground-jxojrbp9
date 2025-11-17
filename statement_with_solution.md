# Programmingtask Digital Root

For a given number `N` calculate the **Digital Root**.

The Digital Root is calculated by summing up all digits of a number. 
E.g. `2025` has a Digital Root of `9` because `2+0+2+5 = 9`

Implement the method `solution(N)` in the code below. 
Chose the programming language of your choice (Python, Java, C, ...) and click on the "Run" Button below the code to start the testscases.

**Constraints:**
0 ≤ N ≤ 1000000000



## PYTHON


```python runnable

def solution(N:int):
    # ---------------------------- #
    # - TODO: ADD YOUR CODE HERE - #
    # ---------------------------- #
    result = 0
    for digit in str(N):
        result = result + int(digit)

    return result


# -------------------------------------------------- #
# ---------- DO NOT MODIFY THE CODE BELOW ---------- #
# -------------------------------------------------- #

INPUTS = [12, 56, 2025, 8, 0, 9999, 17112025]
CHECKS = [1656302624, 3832185857, 3205138698, 2846111786, 3158815156, 3540719418, 3071405752]

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
print(f"SUCCESS: congratulations, you solved the task at {datetime.now()+ timedelta(hours=1)}")

```

## JAVA

```java runnable
import java.util.Date;
public class Main {
  public static int solution(int N) {
    /* ---------------------------- */
    /* - TODO: ADD YOUR CODE HERE - */
    /* ---------------------------- */
    int result = 0;
    String numString = Integer.toString(N);
    for (int i=0; i<numString.length(); i++) {
        result += Integer.parseInt(numString.substring(i,i+1));
    }

    return result;
  }


  /* -------------------------------------------------- */
  /* ---------- DO NOT MODIFY THE CODE BELOW ---------- */
  /* -------------------------------------------------- */

  public static void main(String[] args) {

    int[] INPUTS = {12, 56, 2025, 8, 0, 9999, 17112025};
    int[] CHECKS = {48690, 1632385, 47655768, 1792, 1536, 1686256803, -151278289};

    for (int i=0; i<INPUTS.length; i++) {
        int N = INPUTS[i];
        int check = CHECKS[i];
        int result = solution(N);
        int chk = (Integer.toString(N)+Integer.toString(result)).hashCode();
        // System.out.println(chk);
        if (chk == check) {
            System.out.println("GOOD: Digital Root for "+N+" is "+result);
        }
        else {
            System.err.println("FAIL: Digital Root for "+N+" is not "+result);
            System.exit(1);
        }    
    }
    System.out.println("------------------------------------------------------------");
    System.out.println("SUCCESS: congratulations, you solved the task at "+new Date().toString());
  }
}
```

## C

```C runnable
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
static int solution(unsigned N) {
    /* ---------------------------- */
    /* - TODO: ADD YOUR CODE HERE - */
    /* ---------------------------- */
    unsigned result = 0;
    unsigned val = N;
    while (val > 0) {
        result += val % 10;
        val /= 10;
    }

    return result;
}


/* -------------------------------------------------- */
/* ---------- DO NOT MODIFY THE CODE BELOW ---------- */
/* -------------------------------------------------- */

int main(void) {
    struct test {
        unsigned input;
        unsigned check;
    };
    struct test tests[] = {
        {12, 762299093}, {56, 1049489039}, {2025, 909320628},
        {8, 462648444}, {0, 1804289383}, {9999, 687175592}, {17112025, 796206383}
    };
    for (int i = 0; i < sizeof(tests) / sizeof(struct test); i++) {
        unsigned N = tests[i].input;
        unsigned check = tests[i].check;
        unsigned result = solution(N);
        srand(tests[i].input + result);
        unsigned chk = rand();
        if (chk == check) {
            printf("GOOD: Digital Root for %u is %u\n", N, result);
        } else {
            // fprintf(stderr, "FAIL: Digital Root for %u is not %u (%u)\n", N, result, chk);
            fprintf(stderr, "FAIL: Digital Root for %u is not %u\n", N, result);
            return 1;
        }
    }
	time_t now = time(NULL);
	now += 60 * 60;
	struct tm *tm = localtime(&now);
	char buf[1024];
	strftime(buf, 1023, "------------------------------------------------------------\n"
		"SUCCESS: congratulations, you solved the task at %a %b %d %H:%M:%S", tm);
	puts(buf);
    return 0;
}
```

## C++

```C++ runnable
#include <iostream>
#include <string>
#include <cstdlib>
#include <ctime>

using namespace std;

int solution(unsigned int N) {
    /* ---------------------------- */
    /* - TODO: ADD YOUR CODE HERE - */
    /* ---------------------------- */
    int result = 0;
    string numStr = to_string(N);
    for (char digit : numStr) {
        result += digit - '0';
    }

    return result;
}

/* -------------------------------------------------- */
/* ---------- DO NOT MODIFY THE CODE BELOW ---------- */
/* -------------------------------------------------- */

int main() 
{
    struct Test {
        unsigned int input;
        unsigned int check;
    };
    
    Test tests[] = {
        {12, 762299093}, {56, 1049489039}, {2025, 909320628},
        {8, 462648444}, {0, 1804289383}, {9999, 687175592}, {17112025, 796206383}
    };
    
    for (int i = 0; i < 7; i++) {
        unsigned int N = tests[i].input;
        unsigned int check = tests[i].check;
        unsigned int result = solution(N);
        srand(tests[i].input + result);
        unsigned int chk = rand();
        if (chk == check) {
            cout << "GOOD: Digital Root for " << N << " is " << result << endl;
        } else {
            cerr << "FAIL: Digital Root for " << N << " is not " << result << endl;
            return 1;
        }
    }
    
    time_t now = time(NULL);
    now += 60 * 60;
    struct tm *tm = localtime(&now);
    char buf[1024];
    strftime(buf, 1023, "SUCCESS: congratulations, you solved the task at %a %b %d %H:%M:%S", tm);
    cout << "------------------------------------------------------------" << endl;
    cout << buf << endl;
    
    return 0;
}
```


## Node.JS

```javascript runnable
function solution(N) {
    // ---------------------------- //
    // - TODO: ADD YOUR CODE HERE - //
    // ---------------------------- //
    let result = 0;
    const numStr = N.toString();
    for (let digit of numStr) {
        result += parseInt(digit);
    }

    return result;
}

// -------------------------------------------------- //
// ---------- DO NOT MODIFY THE CODE BELOW ---------- //
// -------------------------------------------------- //

const INPUTS = [12, 56, 2025, 8, 0, 9999, 17112025];
const CHECKS = [1656302624, -462781439, -1089828598, -1448855510, -1136152140, -754247878, -1223561544];

const crypto = require('crypto');

for (let i = 0; i < INPUTS.length; i++) {
    const N = INPUTS[i];
    const check = CHECKS[i];
    const result = solution(N);
    
    const hash = crypto.createHash('md5').update(`${N}${result}`).digest();
    const chk = ((((hash[3] << 8) + hash[2]) << 8) + hash[1] << 8) + hash[0];
    
    if (chk === check) {
        console.log(`GOOD: Digital Root for ${N} is ${result}`);
    } else {
        console.error(`FAIL: Digital Root for ${N} is not ${result}`);
        process.exit(1);
    }
}

console.log("------------------------------------------------------------");
const now = new Date();
now.setHours(now.getHours() + 1);
console.log(`SUCCESS: congratulations, you solved the task at ${now}`);
```


## C# 

```C# runnable
using System;

class Program 
{
    static int solution(int N) 
    {
        /* ---------------------------- */
        /* - TODO: ADD YOUR CODE HERE - */
        /* ---------------------------- */
        int result = 0;
        string numString = N.ToString();
        foreach (char digit in numString) 
        {
            result += int.Parse(digit.ToString());
        }

        return result;
    }

    /* -------------------------------------------------- */
    /* ---------- DO NOT MODIFY THE CODE BELOW ---------- */
    /* -------------------------------------------------- */

    static void Main() 
    {
        int[] INPUTS = {12, 56, 2025, 8, 0, 9999, 17112025};
        int[] CHECKS = {289116474, 1449066918, 202469091, -1193887400, 1479163514, 1399327101, 1342042333};

        for (int i = 0; i < INPUTS.Length; i++) 
        {
            int N = INPUTS[i];
            int check = CHECKS[i];
            int result = solution(N);
            int chk = (N.ToString() + result.ToString()).GetHashCode();
            
            if (chk == check) 
            {
                Console.WriteLine($"GOOD: Digital Root for {N} is {result}");
            }
            else 
            {
                Console.Error.WriteLine($"FAIL: Digital Root for {N} is not {result}");
                Environment.Exit(1);
            }    
        }
        
        Console.WriteLine("------------------------------------------------------------");
        Console.WriteLine($"SUCCESS: congratulations, you solved the task at {DateTime.Now.AddHours(1)}");
    }
}
```

## GO

```go runnable
package main

import (
	"crypto/md5"
	"encoding/binary"
	"fmt"
	"os"
	"time"
	"strconv"	
)

func solution(N int) int {
	// ---------------------------- //
	// - TODO: ADD YOUR CODE HERE - //
	// ---------------------------- //
	result := 0
	numStr := strconv.Itoa(N)
	for _, digit := range numStr {
		digitVal, _ := strconv.Atoi(string(digit))
		result += digitVal
	}

	return result
}

// -------------------------------------------------- //
// ---------- DO NOT MODIFY THE CODE BELOW ---------- //
// -------------------------------------------------- //

func main() {
	INPUTS := []int{12, 56, 2025, 8, 0, 9999, 17112025}
	CHECKS := []uint32{1656302624, 3832185857, 3205138698, 2846111786, 3158815156, 3540719418, 3071405752}

	for i, N := range INPUTS {
		check := CHECKS[i]
		result := solution(N)
		
		hash := md5.Sum([]byte(fmt.Sprintf("%d%d", N, result)))
		chk := binary.LittleEndian.Uint32(hash[:4])
		
		if chk == check {
			fmt.Printf("GOOD: Digital Root for %d is %d\n", N, result)
		} else {
			fmt.Fprintf(os.Stderr, "FAIL: Digital Root for %d is not %d\n", N, result)
			os.Exit(1)
		}
	}
	
	fmt.Println("------------------------------------------------------------")
	now := time.Now().Add(time.Hour)
	fmt.Printf("SUCCESS: congratulations, you solved the task at %s\n", now.Format(time.RFC1123))
}
```


## BASH

```bash runnable
function solution {
	N=$1
	############################
	# TODO: ADD YOUR CODE HERE #
	############################
	result=0
	val=$N
	
	while test $val -gt 0; do
		((result+=val%10))
		((val/=10))
	done

	echo $result
}

##################################################
########## DO NOT MODIFY THE CODE BELOW ##########
##################################################

function main {
	local INPUTS=(12 56 2025 8 0 9999 17112025)
	local CHECKS=(52696 113217 74532 148306 64833 67628 30678)
	local i=0
	while test $i -lt ${#INPUTS[@]}; do
		local N=${INPUTS[$i]}
		local check=${CHECKS[$i]}
		local result="$(solution $N)"
		local chk=`echo $result:$N | md5sum | sed 's/-//'`
		chk=$((16#$chk))
		((chk=(chk>>32)+(chk&((1<<32)-1))))
		((chk=(chk>>16)+(chk&((1<<16)-1))))
		if test $chk = $check; then
			echo "GOOD: Digital Root for $N is $result"
		else
			echo "FAIL: Digital Root for $N is not $result" >&2
			exit 1
		fi
		((i++))
	done
	sec=`date +%s`
	((sec+=60*60))
	echo ------------------------------------------------------------
	echo -n 'SUCCESS: congratulations, you solved the task at '
	date --date=@$sec '+%a %b %d %H:%M:%S'
}

main
```

## VB.NET

```vb.net runnable
Imports System

Public Module Program
    Function solution(N As Integer) As Integer
        ' ---------------------------- '
        ' - TODO: ADD YOUR CODE HERE - '
        ' ---------------------------- '
        Dim result As Integer = 0
        Dim numString As String = N.ToString()
        For Each digit As Char In numString
            result += Integer.Parse(digit.ToString())
        Next

        Return result
    End Function

    ' -------------------------------------------------- '
    ' ---------- DO NOT MODIFY THE CODE BELOW ---------- '
    ' -------------------------------------------------- '

    Sub Main()
        Dim INPUTS() As Integer = {12, 56, 2025, 8, 0, 9999, 17112025}
        Dim CHECKS() As Integer = {289116474, 1449066918, 202469091, -1193887400, 1479163514, 1399327101, 1342042333}

        For i As Integer = 0 To INPUTS.Length - 1
            Dim N As Integer = INPUTS(i)
            Dim check As Integer = CHECKS(i)
            Dim result As Integer = solution(N)
            Dim chk As Integer = (N.ToString() + result.ToString()).GetHashCode()
            
            If chk = check Then
                Console.WriteLine("GOOD: Digital Root for "+N.ToString()+" is "+result.ToString())
            Else
                Console.Error.WriteLine("FAIL: Digital Root for "+N.ToString()+" is not "+result.ToString())
                Environment.Exit(1)
            End If
        Next
        
        Console.WriteLine("------------------------------------------------------------")
        Console.WriteLine("SUCCESS: congratulations, you solved the task at "+DateTime.Now.AddHours(1).ToString())
    End Sub
End Module
```

## Kotlin


```kotlin runnable
import java.util.Date
import java.security.MessageDigest

fun solution(N: Int): Int {
    // ---------------------------- //
    // - TODO: ADD YOUR CODE HERE - //
    // ---------------------------- //
    var result = 0
    val numString = N.toString()
    for (digit in numString) {
        result += digit.toString().toInt()
    }

    return result
}

// -------------------------------------------------- //
// ---------- DO NOT MODIFY THE CODE BELOW ---------- //
// -------------------------------------------------- //

fun main(args: Array<String>) {
    val INPUTS = listOf(12, 56, 2025, 8, 0, 9999, 17112025)
    val CHECKS = listOf(1656302624L, 3832185857L, 3205138698L, 2846111786L, 3158815156L, 3540719418L, 3071405752L)
    
    for (i in INPUTS.indices) {
        val N = INPUTS[i]
        val check = CHECKS[i]
        val result = solution(N)
        
        val md = MessageDigest.getInstance("MD5")
        val hash = md.digest("$N$result".toByteArray())
        val chk = (((hash[3].toLong() and 0xFF shl 8) + (hash[2].toLong() and 0xFF) shl 8) + (hash[1].toLong() and 0xFF) shl 8) + (hash[0].toLong() and 0xFF)
        
        if (chk == check) {
            println("GOOD: Digital Root for $N is $result")
        } else {
            System.err.println("FAIL: Digital Root for $N is not $result")
            System.exit(1)
        }
    }
    
    println("------------------------------------------------------------")
    println("SUCCESS: congratulations, you solved the task at ${Date(System.currentTimeMillis() + 3600000)}")
}
```
