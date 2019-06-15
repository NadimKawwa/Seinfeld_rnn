# Seinfeld Recurrent Neural Networks



![seinfeld_cast](https://github.com/NadimKawwa/Seinfeld_rnn/blob/master/pictures/cast.jpg)

In this repository we will generate Seinfeld scripts using recurrent neural networks built on pytorch.
The dataset is found on kaggle and free to to download [here](https://www.kaggle.com/thec03u5/seinfeld-chronicles#scripts.csv).

## Requirements

The scripts are written in python 3 and require the following libraries:
- torch
- numpy

## Preprocessing

This step involves creating a lookup table that returns two dictionaries:
- integer to vocab
- vocab to integer

Next we split the script into a word array using spaces as delimiters. However, punctuations like periods and exclamation marks can create multiple ids for the same word. For example, "bye" and "bye!" would generate two different word ids.

We implement a function  to return a dictionary that will be used to tokenize symbols like "!" into "||Exclamation_Mark||", our list is therefore:

Period ( . )
Comma ( , )
Quotation Mark ( " )
Semicolon ( ; )
Exclamation mark ( ! )
Question mark ( ? )
Left Parentheses ( ( )
Right Parentheses ( ) )
Dash ( - )
Return ( \n )

This dictionary will be used to tokenize the symbols and add the delimiter (space) around it. This separates each symbols as its own word, making it easier for the neural network to predict the next word. 


## Building the Model

We create a RNN class using torch's [Module class](https://pytorch.org/docs/master/nn.html#torch.nn.Module) and using LSTM cells. The list below are hyperparameters used to tune the network's performance.

- sequence_length: the length of a sequence.
- batch_size: the batch size.
- num_epochs:the number of epochs to train for.
- learning_rate: the learning rate for an Adam optimizer.
- vocab_size: the number of uniqe tokens in our vocabulary.
- output_size: the desired size of the output.
- embedding_dim: the embedding dimension; smaller than the vocab_size.
- hidden_dim: the hidden dimension of your RNN.
- n_layers: the number of layers/cells in your RNN.

## Results


The interaction below is a selected result of the network. There are some random words, some sentences make sense, none compare to the original show.

'''

kramer: moral notion" i don't know how much i have to find this manner to die.

hoyt: call matt vogel.

hoyt: uromycitisis"

hoyt: so what do you think"

jerry: i think you liked the pilot.

elaine: oh. yeah.

jerry: i think it's a very incriminating name. i mean, i was employed in puerto rico.

jerry: i thought you said that was a good idea.

jerry: oh, no. no no no no no no. i don't think i should go out to mario's movies in the middle of the eighth inning to proceed, the virgin bystander is.

hoyt: uromycitisis.

elaine: well, i was in snitzer's bakery. i can't be able to grow up.

kramer: oh, i think that's not the point of a prostitute. i think i could accept that pilot. i was screamin' to capture to find a character in the united county, october 7th, 1992! swarm! swarm! gammy!!

kramer: well, i'm sorry, you can hear this.

kramer: oh, you know, you have a boyfriend in the eighth.

jerry: oh, you know, the whole life is still reeling.

hoyt: call me alone.

elaine: well, i was a little presumptuous in the eighth department.

george: you know i was in the bathroom.

jerry: i know.

jerry: what"

kramer: yeah, sure! what is this"

hoyt: no, no, no. no. i mean that is a problem. it's a little adjustment.

hoyt: so how was it"

george: i don't know how much i got.

hoyt: uromycitisis.

hoyt: so i stood up the loading zone. they loved the article.

jerry: i think i would know how you need any of those things, or something"

george: yes.

elaine: i was screamin' for jumping in the bathroom.

'''
