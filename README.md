# Scalable Book Recommendation System: Optimized Cosine Similarity Computation for Large Sparse Datasets

## Overview
This project demonstrates the implementation of a highly efficient and scalable book recommendation system. It leverages an optimized cosine similarity computation for processing large sparse datasets, addressing memory constraints and computational bottlenecks encountered in traditional methods.

The recommendation system is designed to analyze a user-book ratings dataset with over **100,000 users** and **270,000 books**, providing personalized book recommendations based on user similarity. The project is implemented in Python with vectorized operations to handle sparse matrices efficiently.

---

## Key Features

- **Optimized Cosine Similarity Computation:**
  - Reimplemented cosine similarity computation using vectorized operations to reduce memory usage and improve scalability.
  - Limited calculations to non-zero indices of user vectors, significantly reducing unnecessary computations.

- **Personalized Recommendations:**
  - Identifies the top-K similar users for each target user.
  - Suggests the top-rated books by similar users that the target user has not yet read.

- **Efficient Sparse Data Processing:**
  - Processes large user-book matrices stored in sparse formats to optimize memory consumption.
  - Converts sparse data to dense formats only for relevant computations.

- **Scalability:**
  - Capable of processing datasets containing millions of user-book interactions.
  - Designed for future integration with distributed systems or cloud platforms for even larger-scale operations.

---

## Dataset

The project uses three main datasets and an intermediate libsvm file generated after preprocessing:

1. **Books Metadata:**
   - CSV file containing book details, such as ISBN, title, and author etc.

Example of book data:

| ISBN        | Title              | Author                | Year | Publisher                |
|-------------|--------------------|-----------------------|------|--------------------------|
| 0195153448  | Classical Mythology | Mark P. O. Morford    | 2002 | Oxford University Press  |
| 0002005018  | Clara Callan        | Richard Bruce Wright  | 2001 | HarperFlamingo Canada    |

2. **Ratings Metadata:**
   - CSV file containing rating details, such as User-ID, ISBN, and Rating.

Example of ratings data:

| User-ID | ISBN       | Rating |
|---------|------------|--------|
| 276725  | 034545104X | 0      |
| 276726  | 0155061224 | 5      |

3. **Ratings Metadata:**
   - CSV file containing user details, such as User-ID, and Age.

Example of user data:

| User-ID | Age |
|---------|-----|
| 1       | 20  |
| 2       | 18  |

4. **User-Book Ratings Matrix:**
   - Stored in sparse format (LIBSVM format).
   - Contains user ratings for various books.
   - Each row represents a unique user, containing the bookID and the corresponding rating the user has given that book.

---

## Project Structure

```
.
├── notebooks
│   └── Book_Recommendation_system.ipynb   # Jupyter Notebook with implementation
├── data
│   ├── Books.csv                     # Metadata for books
│   ├── Users.csv                     # Metadata for users
│   ├── Ratings.csv                   # Metadata for ratings
│   └── UserBookMatrix.libsvm         # Intermediate dataset generated that contains the sparse matrix in LIBSVM format
├── output
│   └── Book_Recommendations.csv      # Final recommendations
├── README.md                         # Project documentation
└── LICENSE                           # License information
```

---

## Installation and Requirements

### Prerequisites
Ensure you have the following installed:

- Python 3.8+
- Required Python libraries:
  - `pandas`
  - `numpy`
  - `scikit-learn`

### Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/your_username/scalable-book-rec-system.git
   cd scalable-book-rec-system
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Place the `Books.csv`, `Users.csv`, `Ratings.csv`, and the `UserBookMatrix.libsvm` files in the `data/` directory.

4. Run the Jupyter notebook for the implementation:
   ```bash
   jupyter notebook notebooks/Book_Recommendation_system.ipynb
   ```

---

## Methodology

1. **Data Preprocessing:**
   - Convert the sparse user-book matrix to a dense format only for relevant computations.
   - Reverse mappings for users and books for readability.

2. **Optimized Similarity Calculation:**
   - Compute cosine similarity only for non-zero indices of the target user's vector.
   - Use vectorized operations for faster computation.

3. **Recommendation Generation:**
   - Identify the top-K similar users for each target user based on cosine similarity.
   - Suggest books with the highest weighted average ratings from these similar users.

4. **Output:**
   - Save the recommendations as a CSV file (`output/Book_Recommendations.csv`).

---

## Results
The system efficiently handles large datasets, generating personalized recommendations while avoiding memory crashes. The optimized similarity computation reduces RAM usage and improves processing speed.

---

## Future Work

- **Integration with Distributed Systems:**
  - Adapt the implementation for distributed frameworks like Apache Spark for handling even larger datasets.

- **Enhanced Recommendation Models:**
  - Experiment with hybrid recommendation systems by incorporating content-based filtering and deep learning models.

---

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

## Author
**Abdul Qayyum Khan**  
Master's Student, Arizona State University  

