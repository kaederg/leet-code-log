In JavaScript, a reference variable cannot be reassigned to a different reference. Instead of using loops, a recursive function has to be created so that ref variables stay within the function scope.

```
var addTwoNumbers = function(l1, l2) {
    var carry = 0;
    var node = new ListNode(0); //tmp node is a neat helper
    function recur(n, n1, n2) {
        if(n1 == null && n2 == null) {
            if(carry > 0) {
                n.next = new ListNode(1);
            }
            return;
        }
        var sum = 0;
        if(n1 != null) {
            sum += n1.val;
            n1 = n1.next;
        }
        if(n2 != null) {
            sum += n2.val;
            n2 = n2.next;            
        }
        sum += carry;
        carry = sum >= 10 ? 1 : 0;
        var next = new ListNode(sum%10);
        n.next = next;
        recur(next, n1, n2);
    }
    recur(node, l1, l2);
    return node.next;
};
```
