
## **Chinese Text Augmentation Tool**



Revision based on https://github.com/jasonwei20/eda_nlp/tree/master/code.

Please refer to it for all the hyperparameters under output.

### **Internal Structure:**

  > * main.py: read in and write out files, feel free to customize it on your own
  > * functions.py: the 4 synonym_replacement, random_insertion, random_deletion, random_swap functions and the gen_eda function that utilizes them all, given the alpha parameters 
  > #### warning: the synonym_replacement is a coarse attempt and may need to be heavily revised if you want a more refined result
  > * cache.py: cache the Chinese Wordnet model's lemmas and the corresponding synonym list for later use (because the lemma search is O(n))


 ### **1. For first use: download the necessary data**

  > Chinese Wordnet (CWN)
  > https://github.com/lopentu/CwnGraph
  > * download cwn_graph.pyobj at https://drive.google.com/file/d/1opGRw490cAizoj2JHzR8UIZME3Mc65Ze/view  (cwn_py arg)
  > * download the GitHub itself. you can git clone it with: (cwngit arg)

          #(shell) 
          git clone https://github.com/lopentu/CwnGraph
          #(colab) 
          !git clone https://github.com/lopentu/CwnGraph


   > Ckiptagger 
   > https://github.com/ckiplab/ckiptagger 
   > * data_utils.download_data_gdown("./") 
   > * this is the ckipdata specified in main.py arguments 

 ### **2. Usage:**
   #### default setting
   ```py
    python3 main.py --input=./aicup_dataset/Train_qa_ans_.json 
        --ckipdata=./ckipdata 
        --cwngit=./CwnGraph 
        --cwn_py=./cwn_graph.pyobj 
        --output=./out.json 
        --num_aug=5     # 5x augmented+1x original
        --alpha_sr=0.1  # synonym_replacement 
        --alpha_ri=0.1  # random insertion (with synonyms)
        --alpha_rs=0.1  # random swap
        --alpha_rd=0.1  # random deletion
        --seed=0        # recommend 1126 lol 
        --save_synonyms=0 # if you want to output a synoym dictionary of the synoyms searched or used, turn it to 1
