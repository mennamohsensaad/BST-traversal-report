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

- briefly **Binary trees** is a special case of trees where each node can have at most 2 children. Also, these children are named: left child or right child. A very useful specialization of binary trees is binary search tree (BST) where nodes are conventionally ordered in a certain manner. By convention, the left children<parent<right children, and this rule propagates recursively across the tree 

- binary search trees (BST), sometimes called ordered or sorted binary trees, are a particular type of container: data structures that store "items" (such as numbers, names etc.) in memory. They allow fast lookup, addition and removal of items, and can be used to implement either dynamic sets of items, or lookup tables that allow finding an item by its key (e.g., finding the phone number of a person by name).
![b](https://github.com/sbme-tutorials/sbe201-bst-traversal-report-mennamohsensaad/blob/master/images/bst.jpeg)

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
![d](https://github.com/sbme-tutorials/sbe201-bst-traversal-report-mennamohsensaad/blob/master/images/delation.png)


void remove( BSTNode *&tree, int data )
{
    if ( isEmpty( tree )) return;

    if ( data == tree->data )
    {
        if ( !isEmpty( tree->left ) && !isEmpty( tree->right ))
        {
            BSTNode *minRight = minNode( tree->right );
            tree->data = minRight->data;
            remove( tree->right, minRight->data );
        } else
        {
            BSTNode *discard = tree;

            if ( isLeaf( tree ))
                tree = nullptr;
            else if ( !isEmpty( tree->left ))
                tree = tree->left;
            else
                tree = tree->right;

            delete discard;
        }

    } else if ( data < tree->data )
        remove( tree->left, data );
    else remove( tree->right, data );
}

logarithmic time O(log(n))




#### Traversal

- [ ] Description
- [ ] Why traversing a tree (applications)
- [ ] Extra: After writing the next subsections add a comparison table between the 4 traversal routines.

- tree traversal (also known as tree search) is a form of graph traversal and refers to the process of visiting (checking and/or updating) each node in a tree data structure, exactly once. Such traversals are classified by the order in which the nodes are visited. The following algorithms are described for a binary tree, but they may be generalized to other trees as well.
there are 4 ways to do so in the BST( pre-order,In-order, Post-order,Breadth-first)


- #((Applications))

Pre-order traversal while duplicating nodes and edges can make a complete duplicate of a binary tree. It can also be used to make a prefix expression (Polish notation) from expression trees: traverse the expression tree pre-orderly.

In-order traversal is very commonly used on binary search trees because it returns values from the underlying set in order, according to the comparator that set up the binary search tree (hence the name).

Post-order traversal while deleting or freeing nodes and values can delete or free an entire binary tree. It can also generate a postfix representation of a binary tree.

##### pre-order

- [ ] Description
- [ ] Implement the logic without using recursion (You may use Psuedo-code)
- [ ] Performance analysis (i.e big-`O` notation)

- it means visiting the numbers or the nodes in the BST by visiting
The Parent Node > The Left Node >The Right Node.
For us to make it in a Stack implementation we should start Pushing the numbers from the Right Sub Tree in the order of:
The Right Node>The Left Node>The Parent Node.
Then we Push the Left Sub Tree after Pushing the Right Sub Tree in the order of:
The Right Node > The Left Node >The Parent Node.
At last we Push the Root.
By doing the above mentioned steps, when we Pop the contents of the Stack it will come out in the Pre-order Traversal as the Stack follows the Last In First Out (LIFO) rule.
So, the Root is Popped out first.
After that, the Left Sub Tree is Popped out with the Parent Node then the Left Node then the Right Node and at last the Right Sub Tree is Popped out in the same manner as the Left Sub Tree.

 ![pre]()

 - void preorder( BSTNode *tree )
{
    if( tree )
    {
        std::cout << "[" << tree->data << "]";
        preorder( tree->left );
        preorder( tree->right );
    }
}


##### In-order

- [ ] Description
- [ ] Implement the logic without using recursion (You may use Psuedo-code)
- [ ] Performance analysis (i.e big-`O` notation)

- It means visiting the numbers or the Nodes in the BST in an ascending order or from the smallest to the biggest number, by visiting
The Left Node > The Parent Node > The Right Node.
For us to make it in a Stack implementation we should start Pushing the numbers from the Right Sub Tree in the order of:
The Right Node>The Parent Node>The Left Node.
Then we Push the Root after Pushing the Right Sub Tree.
At Last we Push the Left Sub Tree in the order of:
The Right Node>The Parent Node >The Left Node.
By doing the above mentioned steps, when we Pop the contents of the Stack it will come out in the In-order Traversal as the Stack follows the Last In First Out (LIFO) rule.
So, the Left Sub Tree is Popped out first with the Left Node then the Parent Node then the Right Node.
After that, the Root is Popped out and at last the Right Sub Tree is Popped out in the same manner as the Left Sub Tree.

![in](https://github.com/sbme-tutorials/sbe201-bst-traversal-report-mennamohsensaad/blob/master/images/inorder.jpg)

- void inorder( BSTNode *tree )
{
    if( tree )
    {
        inorder( tree->left );
        std::cout << "[" << tree->data << "]";
        inorder( tree->right );
    }
}




##### Post-order

- [ ] Description
- [ ] Implement the logic without using recursion (You may use Psuedo-code)
- [ ] Performance analysis (i.e big-`O` notation)


- it means visiting the numbers or the nodes in the BST by visiting
The Left Node >The Right Node > The Parent Node.
For us to make it in a Stack implementation we should start Pushing the Root First.
Then we Push the Right Sub in the order of:
The Parent Node > The Right Node >The Left Node.
At last we Push the Left Sub Tree in the order of:
The Parent Node > The Right Node >The Left Node.
By doing the above mentioned steps, when we Pop the contents of the Stack it will come out in the Post-order Traversal as the Stack follows the Last In First Out (LIFO) rule.
So, the Left Sub Tree is Popped out first with the Left Node then the Right Node then the Parent Node.
After that, the Right Sub Tree is Popped out with the Left Node then the Right Node then the Parent Node and at last the Root is Popped out.


![post] ()

- void postorder( BSTNode *tree )
{
    if( tree )
    {
        postorder( tree->left );
        postorder( tree->right );
        std::cout << "[" << tree->data << "]";
    }
}



##### Breadth-first

- [ ] Description
- [ ] Implement the logic without using recursion (You may use Psuedo-code)
- [ ] Performance analysis (i.e big-`O` notation)

_ it mean  that Trees can also be traversed in level-order, where we visit every node on a level before going to a lower level. This search is referred to as breadth-first search (BFS), as the search tree is broadened as much as possible on each depth before going to the next depth.

![Bf]()


### References

- [ ] List the references.
- [ ] Add videos or blogs you think very simple and informative.

1. [Binary search tree](https://en.wikipedia.org/wiki/Binary_search_tree), *Wikipedia*.
2. [Binary tree](https://en.wikipedia.org/wiki/Binary_tree)
3. [Tree traversal] (https://en.wikipedia.org/wiki/Tree_traversal)
4. [*and so on..*]
