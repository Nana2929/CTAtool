Data Augmentation in Chinese

Revision based on https://github.com/jasonwei20/eda_nlp/tree/master/code


*main.py: read in and out, feel free to customize it
*functions.py: the 4 synonym_replacement, random_insertion, random_deletion, random_swap functions and the gen_eda function that utilize them all given the alpha parameters

Usage: 
First use: 
1. download the necessary datas for Chinese Wordnet and ckip word segmentation tagger 
(1) Chinese Wordnet (CWN)
https://github.com/lopentu/CwnGraph
# download cwn_graph.pyobj (https://drive.google.com/file/d/1opGRw490cAizoj2JHzR8UIZME3Mc65Ze/view)
# download the GitHub itself, you can git clone it with: 
# (shell) git clone https://github.com/lopentu/CwnGraph
# (colab) !git clone https://github.com/lopentu/CwnGraph

(2) Ckiptagger 
https://github.com/ckiplab/ckiptagger
# data_utils.download_data_gdown("./") 
# this is the ckipdata specified in main arguments 

2. 
python3 main.py --input=aicup_dataset/Train_qa_ans_.json --ckipdata=./ckipdata --cwngit=./CwnGraph --cwn_py=./cwn_graph.pyobj --output=out.json --num_aug=5 --alpha_sr=0.1 --alpha_ri=0.1 --alpha_rs=0.1 --alpha_rd=0.1 --seed=1126 --save_synonyms=1