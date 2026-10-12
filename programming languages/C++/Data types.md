## - pair class
- included in #include<utility>
- <algorithm> and <vector> already include <utility> so they can be used instead
- template <class T1, class T2> struct pair
- T1 is access by first and T2 is accessed by second
- used with vector often:
typedef pair<int, int> p;
vector<p> arr;

vector<pair<int, int>> arr;

- you can compare it with the comparison operators. If the first one is the same the second one is automatically used

## - std::vector
- can increase and decrease dynamically
- syntax:
template std::vector<type> vec;
- can insert elements with .push_back()
- can get the size with .size()
however this is the number of objects in the vector, not necessarily the storage capacity
- can insert elements in a position with .insert(iterator, value)
- the iterator can be gotten with .begin()+index