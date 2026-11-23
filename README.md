# session-14



### 1. `parking_fee.c`

```c
// parking_fee.c - Calculate parking fee with first hour free (23/11/2026)
#include <stdio.h>

int main() {
    char vehicle_type;
    int hours, fee = 0;

    // take vehicle type and hours from user
    printf("Enter vehicle type (T/F) and hours: ");
    scanf(" %c %d", &vehicle_type, &hours);

    // check if hours are valid
    if (hours < 1) {
        printf("Error: Hours must be at least 1\n");
        return 1;
    }

    // calculate fee (first hour free)
    if (vehicle_type == 'T' || vehicle_type == 't') {
        fee = (hours - 1) * 10;
        printf("Parking Fee: Rs.%d\n", fee);
    } else if (vehicle_type == 'F' || vehicle_type == 'f') {
        fee = (hours - 1) * 30;
        printf("Parking Fee: Rs.%d\n", fee);
    } else {
        printf("Error: Invalid vehicle type\n");
    }

    return 0;
}

```

---

### 2. `parking_fee_bugs.c`

```c
#include <stdio.h>

int main() {
    char t;
    int h, f = 0;

    printf("Enter vehicle type (T/F) and hours: ");
    scanf(" %c %d", &t, &h);

    if (h < 1) {
        printf("Error: Hours must be at least 1\n");
        return 1;
    }

    if (t == 'T' || t == 't') {
        f = (h - 1) * 10;
        printf("Parking Fee: Rs.%d\n", f);
    } else if (t == 'F' || t == 'f') {
        f = (h - 1) * 30;
        printf("Parking Fee: Rs.%d\n", f);
    } else {
        printf("Error: Invalid vehicle type\n");
    }

    return 0;
}

```

---

### 3. `error_log.txt`


parking_fee_bugs.c:7:5: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'printf'
parking_fee_bugs.c:18:14: error: 'hrs' undeclared (first use in this function)
parking_fee_bugs.c:24:1: error: expected declaration or statement at end of input

```

---

### 4. `debug_run.txt`


--- Before Fixing ---
Warning: format '%d' expects argument of type 'int *', but argument 3 has type 'int'
Enter vehicle type (T/F) and hours: F 3
Debug: vehicle = F, hours = 0
Segmentation fault (core dumped)

(After fixing &h, logic error output:)
Enter vehicle type (T/F) and hours: F 3
Debug: vehicle = F, hours = 3
Parking Fee: Rs.90

--- After Fixing ---
Enter vehicle type (T/F) and hours: F 3
Parking Fee: Rs.60

```

---

### 5. Git Push Commands

```bash
gcc -Wall parking_fee.c -o parking_fee
git add parking_fee
git commit -m "Add parking_fee lab files"
git push

```
