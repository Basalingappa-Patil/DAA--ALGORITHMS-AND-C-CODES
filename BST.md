## code
```cpp
#include <iostream>
#include <cstdlib>
#include<set>
using namespace std;

struct tree {
    int data;
    struct tree* left;
    struct tree* right;
};

typedef struct tree TREE;

class BST {
public:
    TREE* insert_into_bst(TREE*, int);
    void inorder(TREE*);
    void preorder(TREE*);
    void postorder(TREE*);
    TREE* delete_from_bst(TREE*, int);

};

// Function to insert a node into the BST
TREE* BST::insert_into_bst(TREE* root, int data) {
    TREE* newnode = (TREE*)malloc(sizeof(TREE));
    if (newnode == NULL) {
        cout << "Memory allocation failed" << endl;
        return root;
    }
    newnode->data = data;
    newnode->left = NULL;
    newnode->right = NULL;

    if (root == NULL) {
        root = newnode;
        cout << "Root node inserted into tree" << endl;
        return root;
    }

    TREE* currnode = root;
    TREE* parent = NULL;

    while (currnode != NULL) {
        parent = currnode;
        if (newnode->data < currnode->data)
            currnode = currnode->left;
        else
            currnode = currnode->right;
    }

    if (newnode->data < parent->data)
        parent->left = newnode;
    else
        parent->right = newnode;

    cout << "Node inserted successfully" << endl;
    return root;
}

// Function to perform inorder traversal
void BST::inorder(TREE* root) {
    if (root != NULL) {
        inorder(root->left);
        cout << root->data << "\t";
        inorder(root->right);
    }
}

// Function to perform preorder traversal
void BST::preorder(TREE* root) {
    if (root != NULL) {
        cout << root->data << "\t";
        preorder(root->left);
        preorder(root->right);
    }
}

// Function to perform postorder traversal
void BST::postorder(TREE* root) {
    if (root != NULL) {
        postorder(root->left);
        postorder(root->right);
        cout << root->data << "\t";
    }
}

// Function to delete a node from the BST
TREE* BST::delete_from_bst(TREE* root, int data) {
    TREE* currnode = root;
    TREE* parent = NULL;
    TREE* successor = NULL;
    TREE* p = NULL;

    if (root == NULL) {
        cout << "Tree is empty" << endl;
        return root;
    }

    while (currnode != NULL && currnode->data != data) {
        parent = currnode;
        if (data < currnode->data)
            currnode = currnode->left;
        else
            currnode = currnode->right;
    }

    if (currnode == NULL) {
        cout << "Item not found" << endl;
        return root;
    }

    if (currnode->left == NULL)
        p = currnode->right;
    else if (currnode->right == NULL)
        p = currnode->left;
    else {
        successor = currnode->right;
        TREE* successorParent = currnode;

        while (successor->left != NULL) {
            successorParent = successor;
            successor = successor->left;
        }

        currnode->data = successor->data;

        if (successorParent->left == successor)
            successorParent->left = successor->right;
        else
            successorParent->right = successor->right;

        free(successor);
        return root;
    }

    if (parent == NULL) {
        free(currnode);
        return p;
    }

    if (currnode == parent->left)
        parent->left = p;
    else
        parent->right = p;

    free(currnode);
    return root;
}




int main() {
    BST bst;
    TREE* root = NULL;
    int choice = 0, data = 0, K = 0;
    int comparisons;

    while (1) {
        cout << "\n ****** MENU ******\n";
        cout << "0. Exit...\n";
        cout << "1. Insert into BST\n";
        cout << "2. Inorder traversal\n";
        cout << "3. Preorder traversal\n";
        cout << "4. Postorder traversal\n";
        cout << "5. Delete from BST\n";


        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
        case 0:
            cout << "Exiting...\n";
            exit(0);
        case 1:
            cout << "Enter the item to insert: ";
            cin >> data;
            root = bst.insert_into_bst(root, data);
            break;

        case 2:
            if (root == NULL)
                cout << "Tree is empty\n";
            else {
                cout << "Inorder traversal is...\n";
                bst.inorder(root);
                cout << endl;
            }
            break;

        case 3:
            if (root == NULL)
                cout << "Tree is empty\n";
            else {
                cout << "Preorder traversal is...\n";
                bst.preorder(root);
                cout << endl;
            }
            break;

        case 4:
            if (root == NULL)
                cout << "Tree is empty\n";
            else {
                cout << "Postorder traversal is...\n";
                bst.postorder(root);
                cout << endl;
            }
            break;

        case 5:
            cout << "Enter the item to be deleted: ";
            cin >> data;
            root = bst.delete_from_bst(root, data);
            break;


        default:
            cout << "Invalid choice.\n";
        }
    }
    return 0;
}
````
