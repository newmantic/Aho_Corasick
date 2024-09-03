# Aho_Corasick


The Aho-Corasick algorithm is a string-searching algorithm that efficiently searches for multiple patterns within a text simultaneously. It combines the concepts of a trie (prefix tree) and a failure function (similar to the one used in the Knuth-Morris-Pratt algorithm) to quickly find all occurrences of any of a set of patterns in a given text.


Trie (Prefix Tree):
A trie is a tree-like data structure where each node represents a single character of a string.
The root node represents an empty string, and paths from the root to a node represent prefixes of the strings (patterns) stored in the trie.

Failure Function:
The failure function is used to handle mismatches efficiently by jumping to the next possible matching state in the trie without having to restart the search from the root.
The failure function allows the algorithm to backtrack in the trie to the longest possible proper suffix that is also a prefix of another pattern.

Output Function:
Each node in the trie may have one or more patterns associated with it (the patterns that end at that node). The output function of a node returns the list of all patterns that end at that node.


Build the Trie:
Insert each pattern into the trie.
For each character in a pattern, traverse the trie from the root, creating a new node if the character is not already present.
Mark the end of the pattern in the trie by associating the pattern with the last node reached.

Build the Failure Function:
Initialize the failure function for each node in the trie using a Breadth-First Search (BFS).
For each node u and character c, if the transition from u to v on c exists, set the failure function fail(v) to be the node corresponding to the longest proper suffix of the string ending at v that is also a prefix of another pattern.
If no such suffix exists, set fail(v) = 0 (the root).

Search the Text:
Traverse the text character by character, following the transitions in the trie.
If a mismatch occurs (i.e., no transition for the current character), follow the failure function to find the next possible match.
If a node is reached that has one or more patterns in its output function, report the occurrence of those patterns at the corresponding position in the text.


Time Complexity
Trie Construction: O(sum(m)) where m is the length of each pattern.
Failure Function Construction: O(sum(m)).
Search: O(n + sum(m)), where n is the length of the text and m is the length of the patterns.
The overall time complexity is O(n + sum(m)), making it very efficient for searching multiple patterns in a large text.
