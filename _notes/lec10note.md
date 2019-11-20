# 10/31 Lecture Note

## Lecture 10 String + Mutable vs Immutable
+ ### string
    + iteration
    ```python
    def print_range( num ):
        for i in range(num):
            if i < 3:
                print(i)
            else:
                if i < 5:
                    continue
                else:
                    return i
    >>> print_range(8)
    0
    1
    2
    5 
    ```
+ ### under the hood
    + everything in python is an object

    + string is immutable
    ```python
    # Example:
    # Trying to modify two string variable in one function

    my_bat = "bat"
    my_cat = "cat"

    ur_bat = "bat"

    def swap_pets (pet1, pet2):
        tmp = pet1
        pet1 = pet2
        pet2 = tmp
        return pet2

    print("Before the swap:", my_cat, my_bat)
    swap_pets(my_cat, my_bat)
    print("After the swap:", my_cat, my_bat)
    ```
    + list is mutable
    ```python
    # Example:
    # Trying to modify a list with two strings inside it
    
    listOfPets = ["cat", "bat"]

    def swap_pets_list (a_list):
        print("From swap:", a_list[0], a_list[1])
        tmp = a_list[1]
        a_list[1] = a_list[0]
        a_list[0] = tmp
        print("From swap:", a_list[0], a_list[1])
        return a_list
    
    print("Before the swap:", listOfPets)
    swap_pets_list(listOfPets)
    print("After the swap:", listOfPets)
    ```

