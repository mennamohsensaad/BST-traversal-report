# Binary Search Tree (BST) Traversal Routines

## Trees

- [ ] Introduce **graphs** briefly and **tree** as a special case of a **graph** data structure.
- [ ] Add some figures for **graphs** and figures for **trees**.

[*Binary Search Tree (BST) Traversal Stack Implementation
The above illustration is called a Binary Search Tree (BST), it begins with the 1st number called Root, and then it branches to the Right and Left Sub Trees, and every node that is branched is called a Parent Node.
Every node without branches is called a Leaf.
The Left Node should always be smaller than the Parent Node, and the Right Node should always be greater than the Parent Node.
so briefly **Binary trees** is a special case of trees where each node can have at most 2 children. Also, these children are named: left child or right child. A very useful specialization of binary trees is binary search tree (BST) where nodes are conventionally ordered in a certain manner. By convention, the left children<parent<right children, and this rule propagates recursively across the tree *]

## Binary Search Trees

- [ ] Binary Trees as a special case of Trees.
- [ ] Binary Search Tree (BST) as a special case of Binary Trees
- [X] Add a an example figures for a Binary Tree
- [ ] Add a an example figures for a BST

<!-- This is a comment line in Markdown and HTML -->
<!-- Comment line are not rendered in the viewed document -->
<!-- Here is a sample images inside a table  -->
| Binary Tree | Binary Search Tree (BST) |
|-------------|--------------------------|
| ![bt](images/sample_image.png) | ![t](https://github.com/sbme-tutorials/sbe201-bst-traversal-report-mennamohsensaad/blob/master/images/tree1.png) |

[*At least two paragraphs here*]

### Motivation

 - [ ] Why using BST
- [ ]BST vs. Arrays
- [ ] BST vs. Linked Lists

- Efficient search & insertion/deletion in logarithmic time O(log(n))

   - Arrays:
        (+) efficient search on sorted arrays O(log(n)),
        (-) ineffiecient insertion/deletion O(n).
    -Linked lists:
        (-) inefficient search O(n),
        (+) efficient insertion/deletion O(1).



### Node Structure

struct BSTNode
{
int data;
    BSTNode *left;
    BSTNode *right;
};
```

### Basic Operations on BST

#### Insertion

- [ ] Description
- [ ] Sample code (Maybe Psuedo)
- [ ] Performance analysis (i.e big-`O` notation)

 Nodes can be inserted into binary trees in between two other nodes or added after a leaf node. In binary trees, a node that is inserted is specified as to which child it is.
 (Leaf nodes) 
To add a new node after leaf node A, A assigns the new node as one of its children and the new node assigns node A as its parent.
 (Internal nodes)
The process of inserting a node into a binary tree
Insertion on internal nodes is slightly more complex than on leaf nodes. Say that the internal node is node A and that node B is the child of A. (If the insertion is to insert a right child, then B is the right child of A, and similarly with a left child insertion.) A assigns its child to the new node and the new node assigns its parent to A. Then the new node assigns its child to B and B assigns its parent as the new node.

 ![i](https://github.com/sbme-tutorials/sbe201-bst-traversal-report-mennamohsensaad/blob/master/images/Insertion.png)


void insert( BSTNode *&tree, int data )
{
    if ( isEmpty( tree ))
        tree = new BSTNode{ data , nullptr , nullptr };

    else
    {
        if ( data < tree->data )
            insert( tree->left, data );

        else insert( tree->right, data );
    }
}

logarithmic time O(log(n))

#### Removal

- [ ] Description
- [ ] Sample code (Maybe Psuedo)
- [ ] Performance analysis (i.e big-`O` notation)

Deletion is the process whereby a node is removed from the tree. Only certain nodes in a binary tree can be removed unambiguously
Node with zero or one children
The process of deleting an internal node in a binary tree

Suppose that the node to delete is node A. If A has no children, deletion is accomplished by setting the child of A's parent to null. If A has one child, set the parent of A's child to A's parent and set the child of A's parent to A's child.
Node with two children
In a binary tree, a node with two children cannot be deleted unambiguously. However, in certain binary trees (including binary search trees) these nodes can be deleted, though with a rearrangement of the tree structure.








#### Traversal

- [ ] Description
- [ ] Why traversing a tree (applications)
- [ ] Extra: After writing the next subsections add a comparison table between the 4 traversal routines.

[*Write here*]

##### In-order

- [ ] Description
- [ ] Implement the logic without using recursion (You may use Psuedo-code)
- [ ] Performance analysis (i.e big-`O` notation)

[*Write here*]

##### Pre-order

- [ ] Description
- [ ] Implement the logic without using recursion (You may use Psuedo-code)
- [ ] Performance analysis (i.e big-`O` notation)

[*Write here*]

##### Post-order

- [ ] Description
- [ ] Implement the logic without using recursion (You may use Psuedo-code)
- [ ] Performance analysis (i.e big-`O` notation)

[*Write here*]

##### Breadth-first

- [ ] Description
- [ ] Implement the logic without using recursion (You may use Psuedo-code)
- [ ] Performance analysis (i.e big-`O` notation)

[*Write here*]

### References

- [ ] List the references.
- [ ] Add videos or blogs you think very simple and informative.

1. [Binary search tree](https://en.wikipedia.org/wiki/Binary_search_tree), *Wikipedia*.
2. [*Reference 2*]
3. [*Reference 3*]
4. [*and so on..*]
