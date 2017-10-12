# mallet-lda-example


Download and extract Mallet 2.x
```
wget http://mallet.cs.umass.edu/dist/mallet-2.0.8.zip
unzip malled-2.0.8.zip
```

Create a file containing one line per document (in this example ap.input)
```
AP891016-0001,ap nr 10 16 89 2347edt 624602820 r a am elpasoshooting     10 16 0314 am el paso shooting 0321 mortally wounded detective kills gunman by suzanne gamboa associated press writer el paso  texas  ap       a detective was shot to death monday by his former business partner in a police fund raising business  authorities said  the gunman was killed by shots fired by the mortally wounded detective...
```

Convert the input documents to Mallet sequence file format:
```
bin/mallet import-file --input ap.input --output ap.seq --keep-sequence
```

Train topics setting the threads, number of topics, and interval for hyper parameter optimization:
```
bin/mallet train-topics --num-threads 10 --input ap.seq  --num-topics 800 \
           --optimize-interval 10 --output-state ap-topic-state.gz \ 
           --output-doc-topics ap-doc-topics.out > ap.log 2>&1 
```

The output-state file contains word/topic distributions and output-doc-topics contain document/topic distributions.

For more information see http://mallet.cs.umass.edu/topics.php
