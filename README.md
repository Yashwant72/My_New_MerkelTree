# My_New_MerkelTree


Introduction To Merkel Trees
Merkle tree is a data structure used to encrypt transactions efficiently and securely. It's made up of the hashes of various data blocks of transactions. Merkle tree also known as hash tree is a data structure used for data verification and synchronization. It is a tree data structure where each non-leaf node is a hash of its child nodes. All the leaf nodes are at the same depth and are as far left as possible. It maintains data integrity and uses hash functions for this purpose. When we have lots of data as separate modules and we want to calculate the hash value of the data we use the Merkel tree. It essentially uses two root nodes and calculates hash for them then the next two parents and so on until the root hash is calculated.One of the uses can be to verify the files received from anonymous sources. On the blockchain we can receive files from varios users and some of them can even be couproted. To overcome this issue we take all the received files and put them as roots of a merkel tree and calculate the root hash for files. Then this root can be sent as parity in order to check whether the files are tampered or not.

Algorithm :

Algorithm of find function in Merkle tree :
Step 1: We will take tree and key as parameters.
Step 2: If the tree is null then we will return null.
Step 3: If the tree->key is equal to the key we will return the tree.
Step 4: If the key is smaller than tree -> key then we will return find (tree  ->left, key)
Step 5: else return find(tree->right, key)

Algorithm to add a node in Merkle tree :
Step 1: We will take key and value as parameters.
Step 2: Take the hash(key) and store it in a variable called index.
Step 3: store (struct node*) arr[index].head in a pointer called tree of datatype node.
Step 4: create a new node with its key as key and value as value and both links as null.
Step 5: If the tree is null then assign the new node to the head and increment the size by 1.
Step 6: If the tree is not null then we will check if the key is already present in the tree using the find function.
Step 7: If the key is already present in the tree then we will update the value.
Step 8: If it is not present in the tree then we will use the insert function to insert the element.

Algorithm of insert function : 
Step 1: It will take tree and item pointers of node data type as parameters.
Step 2: If item->key is smaller than tree->key and tree->left is null then assign the item to tree->left.
Step 3: If item->key is smaller than tree->key and tree->left is not null then call insert function with tree->left and item as parameters.
Step 4: If item->key is greater than tree->key and tree->right is null then assign the item to tree->right.
Step 5: If item->key is greater than tree->key and tree->right is not null then call insert function with tree->right and item as parameters.

Algorithm to delete a node in Merkle tree : 
Step 1: We will take a key as a parameter.
Step 2: Take the hash(key) and store it in a variable called index.
Step 3: store (struct node*) arr[index].head in a pointer called tree of datatype node.
Step 4: If the tree is null then the key is not present.
Step 5: If the tree is not null then we will check if the key is already present in the tree using the find function.
Step 6: If the find function returns null then the key is not present in the tree.
Step 7: If it is not null then we will use the remove function to delete the element.
Algorithm of remove function :
Step 1: It will take tree and key as parameters.
Step 2: If the tree is null then return null.
Step 3: If the key is smaller than the tree->key then tree->left is equal to remove(tree->left, key) and return tree.
Step 4: If the key is greater than the tree->key then tree->right is equal to remove(tree->right, key) and return tree.
Step 5: else if the tree->left is equal to null and the tree->right is equal to null then decrement the size and return tree->left.
Step 6: else if the tree->left is not equal to null and the tree->right is equal to null then decrement the size and return tree->left.
Step 7: else if tree->left is equal to null and tree->right is not equal to null then decrement the size and return tree->right.
Step 8: else assign tree->left to a pointer called left of data type node.
Step 9: While left->right is not equal to null, left is equal to left->right.
Step 10: tree->key is equal to left->key.
Step 11: tree->value is equal to left->value.
Step 12: tree->left is equal to remove(tree->left, tree->key).
Step 13: Return tree.
