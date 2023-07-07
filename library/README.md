# Library

This case study is a program that can be used in a small library to include new books
in the library, to check out books to people, and to return them.
As this program is a practice in the use of linked lists, almost everything is implemented in terms of such lists. But to make the program more interesting, it uses
linked lists of linked lists that also contain cross-references (see Figure 3.26).
First, there could be a list including all authors of all books in the library. However, searching through such a list can be time-consuming, so the search can be sped
up by choosing at least one of the two following strategies:
■ The list can be ordered alphabetically, and the search can be interrupted if we
find the name, if we encounter an author’s name greater than the one we are
searching for, or if we reach the end of list.
■ We can use an array of pointers to the author structures indexed with letters;
each slot of the array points to the linked list of authors whose names start with
the same letter.
The best strategy is to combine both approaches. However, in this case study,
only the second approach is used, and the reader is urged to amplify the program by
adding the first approach. Note the articles a, an, and the at the beginning of the titles
should be disregarded during the sorting operation.
The program uses an array catalog of all the authors of the books included
in the library and an array people of all the people who have used the library at
least once. Both arrays are indexed with letters so that, for instance, position
catalog[‘F’] refers to a linked list of all the authors whose names start with F.
Because we can have several books by the same author, one of the data members of the author node refers to the list of books by this author that can be found
in the library. Similarly, because each patron can check out several books, the
node corresponding to this patron contains a reference to the list of books currently
checked out by this patron. This fact is also indicated by setting the patron member of the checked-out book to the node pertaining to the patron who is taking the
book out.
Books can be returned, and that fact should be reflected by removing the appropriate nodes from the list of the checked-out books of the patron who returns them.
The patron member in the node related to the book that is being returned has to be
reset to null.
