# Floyd's cycle detection algorithm

This is an algorithm used to figure out if there is a cycle in a linked list.

Base Case
- ![Image](/dsa/assets/287_base_case.JPG)

Move `slow` and `fast` pointer until they meet
- ![Image](/dsa/assets/287_meet_up.JPG)

Create a slow2 and then move both slow and slow2 until they meet.
- ![Image](/dsa/assets/287_meet_up.JPG)

Proof:

Although incomplete, this would be the most complete version. Taken from [stackoverflow](https://cs.stackexchange.com/questions/10360/floyds-cycle-detection-algorithm-determining-the-starting-point-of-cycle)

![Image](/dsa/assets/287_proof.JPG)

### Source
[YouTube Video](https://www.youtube.com/watch?v=PvrxZaH_eZ4&ab_channel=Insidecode)