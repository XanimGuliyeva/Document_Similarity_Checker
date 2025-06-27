MinHash & LSH for Document Similarity Detection
This project demonstrates how to use MinHash and Locality-Sensitive Hashing (LSH) to efficiently detect similar documents in the 20 Newsgroups dataset. It includes:

📦 Downloading and extracting the dataset from Google Drive

🧹 Preprocessing: tokenization, stopword removal, and shingling

🧠 MinHash signature generation

⚡ Fast similarity search using LSH

📊 Jaccard similarity computation for candidate verification


🔧 Technologies Used

Python,
datasketch for MinHash & LSH,
nltk for text preprocessing,
gdown for downloading from Google Drive.

📁 Output

The script prints:
Tokenized and shingled documents
MinHash signatures
Candidate similar document pairs
Verified similar pairs with Jaccard similarity scores
