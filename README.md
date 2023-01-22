# Vector Search
The course Vector Search is given in Princeton Fall semester 2023 by

* [Edo Liberty](https://scholar.google.com/citations?user=QHS_pZAAAAAJ&hl=en), the Founder and CEO of [Pinecone](www.pinecone.io), the world's leading Vector Database.

* [Matthijs Douze](https://scholar.google.com/citations?user=0eFZtREAAAAJ&hl=en]) the creator and lead maintainer of [FAISS](https://github.com/facebookresearch/faiss) the most popular and advanced open source library for vector search.


The course covers the core concepts, algorithms, and data structures used for modern vector search systems and platforms. An advanced undergraduate or graduate student with some hands-on experience in linear algebra, probability, algorithms, and data structures should be able to follow this course.


## Abstract

Vector search is a fundamental tool for systems that manipulate large collections of media: search engines, knowledge bases, content moderation tools, recommendation systems, etc.
The discipline lays at the intersection of Artificial Intelligence and Database management systems. 
This course will cover the scientific foundations and practical implementation of vector search systems. 
It will cover the feature extraction from input media, the fundamental algorithms (clustering, quantization, hashing), major vector indexing methods with their tradeoffs.
The course will be evaluated with an exam and a project. 


## Syllabus

**The class contents below are tentative.**


1. Generalities 
	* Embeddings as an information bottleneck. Instead of learning end-to-end, use embeddings as an intermediate representation.
	* Typical volumes of data and scalability. Embeddings are the only way to manage / access large databases. Similarity search is cost effective.
	* The embedding contract. The embedding extractor and embedding indexer agree on the meaning of the distance. Separation of concerns.
	* The vector space model in information retrieval
	* Vector embeddings in machine learning
	
1. Text embeddings
	* 2-layer word embeddings. Word2vec and fastText, obtained via a factorization of a co-ocurrence matrix. Embedding arithmetic: king + woman - man = queen, (already based on similairty search).
	* Sentence embeddings: How to train, masked LM. Properties of sentence embeddings.
	* Large Language Models: reasoning as an emerging property of a LM. What happens when training set = the whole web.

1. Image embeddings 
	* Pixel structures of images. Early works on direct pixel indexing.
	* Traditional CV models. Global descriptors (GIST). Local descriptors (SIFT and friends). Direct indexing of local descriptors for image matching, local descriptor pooling (Fisher, VLAD).
	* Convolutional Neural Nets. Off-the-shelf models. Trained specifically (constrastive learning, self-supervised learning). 
	* Advanced computer vision models 

1. Practical indexing
	* How an index works: basic functionalities (search, add). Optional functionalities: snapshot, incremental add, remove.
	* k-NN search vs. range search 
	* Criteria: Speed / accuracy / memory usage / updateability / index construction time 
	* Computing platform: local / service / CPU / GPU 

1. Mathematical foundations
	* Recap of relevant Linear Algebra
	* Vector operations and notation
	* Probabilistic inequalities	

1. Low dimensional vector search 
	* k-d tree
	* Concentration phenomena
	* Curse of dimensionality

1. Dimensionality Reduction I
	* Principal Components Analysis 
	* Fast PCA algorithms 

1. Dimensionality Reduction II
	* Random Projections
	* Fast Random Projections	

1. Locality Sensitive Hashing
	* Definition of ANN
	* LSH Algorithm
	* LSH Analysis
	
1. Clustering
	* Semantic clustering: properties (purity, as aid for annotation)
	* Clustering from a similarity graph (spectral clustering)
	* Vector clustering: mean squared error criterion. Tradeoff with number of clusters
	* Relationship between vector clustering and quantization (OOD extension) 

1. Vector quantization 
	* Lloyd's optimality conditions. 
	* The k-means algorithm 
	* Exact k-means 
	* Initialization strategies (kmeans++, progressive dimensions with PCA)
	
1. Quantization for lossy vector compression
	* Vector quantization is a topline (directly optimizes the objective)
	* Binary quantization and hamming comparison 
	* Product quantization. Chunked vector quantization. Optimized vector quantization
	* Additive quantization. Extension of product quantization. Difficult to train: approximations (Residual quantization, CQ, TQ, LSQ, etc.)

1. Non-exhaustive search 
	* Early works on bag-of-visual-words inspiration, using quantization. 
	* Voronoi diagram with search buckets.
	* The inverted file model. Relationship with sparse matrices.
	* Cost of coarse quantization vs. inverted list scanning. 

1. Graph based indexes
	* Early works: hierarchical k-means 
	* Neighborhood graphs. How to construct them. NNdescent. 
	* Greedy search in Neighborhood graphs. That does not work -- need long jumps. 
	* HNSW. A practical hierarchical graph-based index.
	* NSG. Evolving a graph k-NN graph.

1. Practical indexing 
	* maintaining top-k results 
	* efficient implementation of brute force search
	* distance computations for product quantization -- tradeoffs. SIMD implementaion
	* Parallelization and distribution -- sharding vs. inverted list distribution.
	* Using co-processors (GPUs).
	* Using a hierachy of memory types (RAM + SSD or RAM + GPU RAM).

1. Advanced topics -- articles to be presented by students
	* Vectors in Generative AI 
	* Neural quantization 
	* Vector Databases 
	* Beyond feature extraction and indexing: neural indexing 
	
1. Project setup

1. Office hours for project work

1. Project Presentations

## Selected literature 

* The product quantization (PQ) method from [“Product quantization for nearest neighbor search”](https://hal.inria.fr/inria-00514462v2/document), Jégou & al., PAMI 2011. This can be seen as a lossy compression technique for high-dimensional vectors, that allows relatively accurate reconstructions and distance computations in the compressed domain.

* The optimized PQ from [“Optimized product quantization”](http://ieeexplore.ieee.org/abstract/document/6678503/), He & al, CVPR 2013. This method can be seen as a linear transformation of the vector space to make it more amenable for indexing with a product quantizer.

* The GPU implementation and fast k-selection is described in [“Billion-scale similarity search with GPUs”](https://arxiv.org/abs/1702.08734), Johnson & al, ArXiv 1702.08734, 2017 

* The HNSW indexing method from ["Efficient and robust approximate nearest neighbor search using Hierarchical Navigable Small World graphs"](https://arxiv.org/abs/1603.09320), Malkov & al., ArXiv 1603.09320, 2016

* The in-register vector comparisons from ["Quicker ADC : Unlocking the Hidden Potential of Product Quantization with SIMD"](https://arxiv.org/abs/1812.09162), André et al, PAMI'19, also used in ["Accelerating Large-Scale Inference with Anisotropic Vector Quantization"](https://arxiv.org/abs/1908.10396), Guo, Sun et al, ICML'20.

* The graph-based indexing method NSG from ["Fast Approximate Nearest Neighbor Search With The Navigating Spreading-out Graph"](https://arxiv.org/abs/1707.00143), Cong Fu et al, VLDB 2019.

* The Local search quantization method from ["Revisiting additive quantization"](https://drive.google.com/file/d/1dDuv6fQozLQFS2AJoNNFGTH499QIp_vO/view), Julieta Martinez, et al. ECCV 2016 and ["LSQ++: Lower running time and higher recall in multi-codebook quantization"](https://openaccess.thecvf.com/content_ECCV_2018/html/Julieta_Martinez_LSQ_lower_runtime_ECCV_2018_paper.html), Julieta Martinez, et al. ECCV 2018.

* The learning based quantizer from ["Unsupervised Neural Quantization for Compressed-Domain Similarity Search"](https://openaccess.thecvf.com/content_ICCV_2019/html/Morozov_Unsupervised_Neural_Quantization_for_Compressed-Domain_Similarity_Search_ICCV_2019_paper.html), Morozov and Banenko, ICCV'19

* Neural indexing from ["Transformer Memory as a Differentiable Search Index"](https://arxiv.org/abs/2202.06991), Tan & al. ArXiV'22

* The hybrid RAM-disk index from ["Diskann: Fast accurate billion-point nearest neighbor search on a single node"](https://proceedings.neurips.cc/paper/2019/hash/09853c7fb1d3f8ee67a61b6bf4a7f8e6-Abstract.html), Subramanya & al. NeurIPS'19

## Build

On unix-like systems with the bibtex and pdflatex available you should be able to do this:


```
git clone git@github.com:edoliberty/vector-search-class-notes.git
cd vector-search-class-notes
./build
```



## Contribute

These class notes are intended to be used freely by academics anywhere, students and professors alike. Please feel free to contribute in the form of pull requests or opening issues.
