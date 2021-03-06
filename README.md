# Word-Context Character Embeddings for Chinese word Segmentation

------

This is the code for the paper "Word-Based Character Embeddings for Chinese word Segmentation".


## Source
Our model could be divided into 2 aspects:
* baseline segmentation model is in the "segmenter" directory.
* word-based character embedding training code is in the "modified-word2vec" dircectory.


## Reguired Softwares
 * CMake
 * Boost
 * glog

## Embedding Training

    
	#Run
	make
    
    
	#Training command

	./seg2vec -train data/small.seg.char.giga \
    	-output  vecs/example.emb \
    	-cbow 0  \
    	-size 50 \
    	-window 5 \
    	-negative 10 \
    	-sample 1e-4 \
    	-threads 6 \
    	-binary 0 \
    	-iter 8 \



## Segmentation Model

	./configure
    make

	mkdir -p model
	mkdir -p log

	GLOG_log_dir=log ./greedy --cnn-mem 999 -i 1 \
    	-T ../../data/pku/small.train.seg \
    	-d ../../data/pku/small.dev.seg \
    	-t ../../data/pku/small.test.seg \
    	--optimizer simple_sgd \
    	--evaluate_stops 2500 \
    	--outfile ctb.test.res \

## Segmentation Parameters
	./greedy -h
        
## Notes:  
* You can find the sample training data in the data directory.
* The performances of crf and greedy models are comparable. 
------


[1]: Hao Zhou, Zhenting Yu, Yue Zhang, Shujian Huang, Xinyu Dai and Jiajun Chen. Word-Context Character Embeddings for Chinese word Segmentation. In Proceeding of EMNLP 2017, short paper.
