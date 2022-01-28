# README #
 
This project was developed by Ali Nazari as his master’s degree project at Boise State University in collaboration with the SLIM team under supervision of Dr. Casey Kennington.
 
### Project Description ###
 
The emerge of Transformers in the field of Natural Language Processing had a sweeping effect and improved the state-of-the-art in most of the NLP tasks. One of the most well-known unsupervised pretrained models for generating general purpose language representation is BERT, standing for Bidirectional Encoder Representations from Transformers. Despite BERT’s popularity and its strength in achieving applaudable results, we believe there is room for improvement. BERT’s most valuable output is a distributional representation of language solely based on textual knowledge. We believe the language is more complex and the lexical semantics are often overlooked in the distributional representation. We like to address this issue and this project takes on the first step which is developing an infrastructure to experiment with variety of solutions. This infrastructure (i.e., a pipeline) incorporates grounded representation of words into a BERT-like model’s distributional representation using wac2vec model. Wac2vec model is based on Words-as-classifiers (WAC) methodology which offers a reliable representation of words that captures their grounded meaning. We test this pipeline against GLUE tasks and evaluate our results in four configurations which the pipeline offers. Although the purpose of this work is not achieving state-of-art results, we were able to successfully fine-tune DistilBERT, a BERT-like model, for GLUE tasks and slightly improve the baseline in couple of tasks. It is expected this pipeline will serve as a foundation for future efforts to improve distributional representation and be beneficial to future projects involving language acquisition by robots and other ongoing projects in Speech, Language & Interactive Machines (SLIM) team.
 
### Set up the pipeline ###
 
#### Instruction
1. Clone the repository
2. Open WAC_BERT_Pipeline.ipynb. You may open it with Google Colab
3. Uncomment the first cell if you are running the pipeline on Google Colab
4. The second 2 cell is to set up the Python environment for the pipeline
  * This Pipeline is set up on Windows 10. You may need different commands to install PyTorch
5. Set the pipeline parameters in the "Parameters" section.
  * Pick BERT-like model at [https://huggingface.co/models](https://huggingface.co/models)
  * Refer to the [project's report](https://scholarworks.boisestate.edu/) to know more about different configurations.
6. Provide input data. An example is in the notebook.
 
	**A.** Write a parser function for your data. There are built-in parsers in *parser.py* module of wac_bert_tools library. The parser function must return a dataframe with two columns ['word','measure']
 
	**B.** Write an argument dictionary to feed to your parser function. e.g. arg={'fname':r"c:\raw_data.csv"}
 
	**C.** Call tokenize.External_Data() and provide its arguments. It returns tokenized data in a Pandas Data Series format
 
	**D.** You may use wac/concreteness function's *.ds2dict()* to convert the data series to a dictionary.
 
7. Provide the training data. Modify the DataProcessor class so it has the same methods and output formats as the provided example. Currently, it is set up for GLUE tasks.
8. Run the remaining cells.
9. Before running the model, the pipeline asks for some information regarding the model you are running to complete the registration. If a name is provided for the model other than the default name, it will save the model.
 
Upon completion of the model, the highest metric value (e.g., accuracy) is saved to the model registry with the epoch in which it was achieved.
 
#### Dependencies
  * numpy
  * pandas
  * transformers
  * torch
  * tqdm
  * wac_bert_tools (found only in this repository)
  >Dependencies to run on GLUE tasks:
  	* datasets
  	* sklearn
 
### Contact ###
The full report on this project can be found [here](https://scholarworks.boisestate.edu/). For further information contact:
* alinazaridaftari@u.boisestate.edu
* caseykennington@boisestate.edu