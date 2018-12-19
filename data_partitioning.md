# Data Partitioning

## 1. Verticle Partitioning

Based on features, for example, store all user information into one server

- Pros: Simple
- Cons: 
  - Scale problem -> huge number of data of one features -> scale to another server
  - Joining multiple table takes long time and cause consistancy problem.

## 2. Region-based Partitioning

Partitioning based on range of data. For example, store the data start with letter "A" in one server and store the data start with letter "B" in another server.

- Pros: Simple, easy to predict the storage requirement
- Cons: data inbalanced, some letter consists more records (solution: combine the letter with less records into one server.)


## 3. Hash-based Partitioning

Paritioning based on hash value. Our hashing function can always map any ID to a number between [1...256], and this number would be the partition we will store our object.

- Pros: balanced split storage.
- Cons: may still cause over-loaded problem (solution: Consistent Hashing)