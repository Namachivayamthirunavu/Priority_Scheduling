# Experiment 2(b): Program to Implement Priority Scheduling

```
Name : Namachivayam T
Reg No : 212223060179
```

## Aim

To write and execute a C program to implement the Priority CPU Scheduling algorithm and calculate the Waiting Time and Turnaround Time for each process along with their average values.

## Algorithm

1. Start.

2. Read the number of processes `n`.

3. Input the Burst Time (BT) and Priority for each process.

4. Assign Process IDs to each process.

5. Sort the processes in ascending order of priority.

   * Smaller priority number indicates higher priority.

6. Initialize the Waiting Time (WT) of the first process as 0.

7. Calculate the Waiting Time for the remaining processes using:

   `WT[i] = WT[i-1] + BT[i-1]`

8. Calculate the Turnaround Time (TAT) for each process using:

   `TAT[i] = WT[i] + BT[i]`

9. Calculate:

   * Average Waiting Time = (Sum of WT) / n
   * Average Turnaround Time = (Sum of TAT) / n

10. Display the Process ID, Priority, Burst Time, Waiting Time, and Turnaround Time.

11. Display the Average Waiting Time and Average Turnaround Time.

12. Stop.

## Procedure for Executing the C Program

* Open a C programming environment such as GCC, Code::Blocks, or Dev-C++.
* Create a new C source file.
* Type or paste the Priority Scheduling program into the editor.
* Save the file with the extension `.c` (e.g., `priority.c`).
* Compile the program and ensure there are no syntax errors.
* Run the program.
* Enter the number of processes, burst times, and priorities.
* Observe the execution order, waiting time, turnaround time, average waiting time, and average turnaround time displayed on the screen.
* Verify that the processes are executed according to their priority, where a smaller priority number represents a higher priority.

## Program

```c
#include <stdio.h>

int main() {
    int n, i, j, temp;
    int bt[20], wt[20], tat[20], p[20], pr[20];
    float avg_wt = 0, avg_tat = 0;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    for(i = 0; i < n; i++) {
        p[i] = i + 1;

        printf("Enter Burst Time for P%d: ", i + 1);
        scanf("%d", &bt[i]);

        printf("Enter Priority for P%d: ", i + 1);
        scanf("%d", &pr[i]);
    }

    for(i = 0; i < n - 1; i++) {
        for(j = i + 1; j < n; j++) {
            if(pr[i] > pr[j]) {
                temp = pr[i];
                pr[i] = pr[j];
                pr[j] = temp;

                temp = bt[i];
                bt[i] = bt[j];
                bt[j] = temp;

                temp = p[i];
                p[i] = p[j];
                p[j] = temp;
            }
        }
    }

    wt[0] = 0;

    for(i = 1; i < n; i++) {
        wt[i] = wt[i - 1] + bt[i - 1];
    }

    for(i = 0; i < n; i++) {
        tat[i] = wt[i] + bt[i];
    }

    printf("\nProcess\tPriority\tBT\tWT\tTAT\n");

    for(i = 0; i < n; i++) {
        printf("P%d\t%d\t\t%d\t%d\t%d\n",
               p[i], pr[i], bt[i], wt[i], tat[i]);

        avg_wt += wt[i];
        avg_tat += tat[i];
    }

    printf("\nAverage Waiting Time = %.2f", avg_wt / n);
    printf("\nAverage Turnaround Time = %.2f\n", avg_tat / n);

    return 0;
}
```

## Output

<img width="541" height="410" alt="image" src="https://github.com/user-attachments/assets/7b8a7819-4ae6-4776-9bdd-e749833c0499" />


## Result

Thus, the C program to implement the Priority CPU Scheduling Algorithm was executed successfully, and the Waiting Time, Turnaround Time, Average Waiting Time, and Average Turnaround Time were calculated and displayed successfully.
