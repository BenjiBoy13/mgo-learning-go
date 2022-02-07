# A taste of string and runes

Go includes strings as a bult in type, the zero value of this type is an empty string; Go also supports unicode as showed on literals document.

Strings can by used with certain comparison and arithmetic operators: 

Operator | Description
-------- | -----------
\==      | Equality
\!=      | Difference
\>, \>=, \<, \<= | Ordering
\+       | Concatenation

Stirngs are inmutable, meaning, you can reassing the value of a string variable but you cannot change the value of the string that is assigned to it. 

As already seen on the literals document Go offers to string types, *string* and *rune* (to store characters: based on int32)

