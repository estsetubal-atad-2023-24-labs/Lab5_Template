# Algorithms and Abstract Data Types

## Lab 5 \| Exercises + Template

🇬🇧 [English version](README_en.md)

This repository was created from:

- <https://github.com/estsetubal-atad/CProgram_Template>

Consult the README if you have questions about its use.

------------------------------------------------------------------------

Goals:

- Use of pointers;

- Passing arguments by reference (vs. passing by copy);

- Dynamic memory management (heap).

References:

- "Linguagem C", e-book available on Moodle.

------------------------------------------------------------------------

❗ The requested functions must be defined and implemented in the `fortnite` module, unless otherwise indicated.

### Level 1 (Estimated duration: &lt; 15min)

1.  Compile and run the program, verifying its execution.

2.  Implement function `bool fortniteItemBuy(const char* name, FortniteItem arr[], int arrLength)` that marks the item with name `name` as purchased (field `owned = true` ).

3.  Implement a code snippet in `main` that asks the user for the name of the item to be purchased. Reprint the store; the item, if found, should appear as purchased; otherwise, it should display an error message. Test the program.

### Level 2 (Estimated duration: ~15min)

4.  Implement function `PtFortniteItem fortniteItemSearch(const char* name, FortniteItem arr[], int arrLength)` that returns the address of the item named `name` ; returns `NULL` if it does not exist.

5.  Modify function `fortniteItemBuy` to use function `fortniteItemSearch` internally. Check that the program retains functionality.

### Level 3 (Estimated duration: ~15min)

6.  Implement function `FortniteItem* fortniteArrayCopy(FortniteItem arr[], int arrLength)` which returns a dynamically allocated array containing a copy of the items in `arr` .

    - Note that it knows exactly the size of the array to be allocated, ie, `arrLength` ; then just copy the items one by one.

7.  Add to `main` the code to test this function; create the copy, print that array and don't forget to free the memory before the program ends.

8.  Use valgring to verify that there are no memory leaks. For convenience, this repository includes the `mem_check.sh` script.

    - No terminal, execute: `$> bash mem_check.sh` .

### Level 4 (Estimated duration: ~30min)

💡 In the next two requested functions, it is not possible to know in advance the size of the array to be allocated; you should increase the size of the array, ie, with `realloc` as necessary.

9.  Implement function `FortniteItem* fortniteFindFreeItems(FortniteItem arr[], int arrLength, int *itemSize)` which:

    - Returns by return a dynamically allocated array with a copy of the free items in the shop, ie, where the field `vbucks == 0` .

    - Returns by reference ( `int *itemSize` ) the number of free items and, consequently, the size of the allocated/returned array.

10. Add in `main` the necessary code to automatically "buy" all free items; the array to be modified is the array created in Level 3. Test the program.

11. Implement and test function `FortniteItem* fortniteFindRarityItems(FortniteItem arr[], int arrLength, const char *rarity, int *itemSize)` which:

    - Returns a dynamically allocated array with a copy of the items whose rarity is the requested one ("string" `rarity` - `const` means that it cannot be changed inside the function);

    - Returns by reference ( `int *itemSize` ) the number of found items and, consequently, the size of the allocated/returned array.

    - 💡 It's a simple adaptation of the `fortniteFindFreeItems` function!

### Level 5 (Estimated duration: &lt; 30min)

12. Implement function `bool fortniteAddNewItem(FortniteItem item, FortniteItem *arr[], int *pArrLength)` which adds a new item `item` to array `arr` . Note that:

    - The value passed by reference ( `FortniteItem *arr[]` ) contains the address of the variable which, in turn, contains the address of the array; this is the only way it can be changed within the function, in case `realloc` changes the block address;

      - The invocation of this function will be done, eg, `bool res = fortniteAddNewItem(<item>, &shop, &shopSize)` - note the passing of the array address ( `&shop` ).

    - The value passed by reference ( `int *pArrLength` ) contains the current store size and will be incremented if the item is successfully added; you will have to dynamically increase the array for that purpose!

    - Returns `true` if the item was successfully added, `false` if more memory cannot be allocated.

    - No item with the same name can exist; return `false` if this situation occurs.

13. Test the previous function and run valgrind.

    - Can you invoke this function on the `shop` array (in stack memory)?

    - What about the store copy (dynamically allocated array)?

    - Do you understand why? Function `realloc` can only be executed on blocks allocated with `malloc/calloc` . 😄

------------------------------------------------------------------------

``` markdown
@bruno.silva
(EOF)
```

\[Disclaimer: This document was automatically translated, some original formatting may have been lost.\]
