'''Write a python program to store second year percentage of students in array.
   Write function for sorting array of floating point numbers in ascending order using
     a) Insertion sort
     b) Shell Sort and display top five scores
'''

def Insertion_Sort(arr):
    n=len(arr)
    if n <= 1:
        return
    for i in range(1, n):
        key = arr[i]
        j = i-1
        while j >= 0 and key < arr[j]:
            arr[j+1] = arr[j]
            j -= 1
        arr[j+1] = key

def Shell_Sort(arr):
    gap = len(arr) // 2
    while gap > 0:
        for i in range(gap, len(arr)):
            temp = arr[i]
            j = i
            while j >= gap and arr[j - gap] > temp:
                arr[j] = arr[j - gap]
                j -= gap
            arr[j] = temp
        gap //= 2

def top_five_per(arr):
    print("Top Five Percentage are : ")
    if len(arr) < 5:
        start, stop = len(arr) - 1, -1
    else:
        start, stop = len(arr) - 1, len(arr) - 6
    for i in range(start, stop, -1):
        print(arr[i],sep = "\n")

arr=[]
n=int(input("Enter Number of Students Whose Percentage to be display: "))
print("Enter percentage for",n,"students (Press ENTER after every students percentage): ")
for i in range(0,n):
    ele=float(input())
    arr.append(ele)

print("The percentage of",n,"students are : ")
print(arr)

flag=1;
while flag==1:
    print("\n---------------MENU--------------")
    print("1. Display Percentage using Insertion Sort")
    print("2. Display Percentage using Shell Sort")
    print("3. EXIT")
    ch=int(input("\n\nEnter your choice (from 1 to 3) : "))

    if ch==1:
        Insertion_Sort(arr)
        a=input("\nDo you want to display top five percentage from the list (yes/no) : ")
        if a=='yes':
            top_five_per(arr)
        else:
            print("\nThanks for using this program!")
            flag=0

    elif ch==2:
        Shell_Sort(arr)
        a=input("\nDo you want to display top five percentage from the list (yes/no) : ")
        if a=='yes':
            top_five_per(arr)
        else:
            print("\nThanks for using this program!")
            flag = 0

    elif ch==3:
        print("\nThanks for using this program!!")
        flag=0

    else:
        print("\nEnter a valid choice!!")
        print("\nThanks for using this program!!")
        flag=0
