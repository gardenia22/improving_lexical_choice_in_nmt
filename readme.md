![Good friend lol](./images/doraemon_nobita.gif)  

This is the code for the paper **Improving Lexical Choice in NMT**. The branches are:  

* master: baseline NMT
* tied_embedding: baseline NMT with tied embedding
* fixnorm: fixnorm model in paper
* fixnorm_lex: fixnorm+lex model in paper
* arthur: apply the method of [Arthur et al.](https://arxiv.org/abs/1606.02006) on top of baseline NMT


To train a model:
* write a configuration function in ```configurations.py```
* run: ```python -m nmt --proto your_config_func```  

Depending on your config function, the code generates a direction under ```nmt/saved_models/your_model_name``` and saves all dev validations there, as well as dev perplexities, train perplexities, best model checkpoint, checkpoint so far (I've tested with saving 1 best checkpoint, not sure about > 1). You should use this checkpoint to translate on any other input.

To translate with UNK replacement:
* run: ```python -m nmt --proto your_config_func --mode translate --unk-repl --model-file path_your_saved_checkpoint.cpkt --input-file path_to_input_file```  

Remember the checkpoint includes data file, meta file, ... but just link to ```.cpkt```, ignore the extension. 