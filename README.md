# little-mallet-wrapper

This is a little Python wrapper around the topic modeling functions of [MALLET](http://mallet.cs.umass.edu/topics.php).

Currently under construction; please send feedback/requests to Maria Antoniak.

See demo.ipynb for a demonstration of how to use the functions in little-mallet-wrapper.


## Documentation

### print_dataset_stats(*training_data*)

| Name               | Type              | Description                      |
| ------------------ | ----------------- | -------------------------------- |
| training_data      | list of strings   | Documents that will be used to train the topic model. |

<br>

### process_string(*text, lowercase=True, remove_short_words=True, remove_stop_words=True, remove_punctuation=True, numbers='replace', stop_words=STOPS*)

| Name               | Type              | Description                      |
| ------------------ | ----------------- | -------------------------------- |
| text      | string   | Individual document to process. |
| lowercase | boolean  | Whether or not to lowercase the text. |
| remove_short_words | boolean | Whether or not to remove words with fewer than 2 characters. |
| remove_stop_words | boolean | Whether or not to remove stopwords. |
| remove_punctuation | boolean | Whether or not to remove punctuation (not A-Za-z0-9) |
| remove_numbers | string | 'replace' replaces all numbers with the normalized token NUM; 'remove' removes all numbers. |
| stop_words | list of strings | Custom list of words to remove. |
| RETURNS | string | Processed version of the input text. |

<br>

### import_data(*path_to_mallet, path_to_training_data, path_to_formatted_training_data, training_data, use_pipe_from=None*)

| Name               | Type              | Description                      |
| ------------------ | ----------------- | -------------------------------- |
| path_to_mallet | string | Path to your local MALLET installation: .../mallet-2.0.8/bin/mallet |
| path_to_training_data | string | Path to where the training data should be stored. |
| path_to_formatted_training_data | string | Path to where the MALLET formatted training data should be stored. |
| training_data | list of strings | Processed documents for training the topic model. |
| use_pipe_from | string | If you want to import the documents using the same model as a previous set of documents, include the path to the previous MALLET formatted training data. |

<br>

### train_topic_model(*path_to_mallet, path_to_formatted_training_data, path_to_model, path_to_topic_key, path_to_topic_distributions, num_topics*)

| Name               | Type              | Description                      |
| ------------------ | ----------------- | -------------------------------- |
| path_to_mallet | string | Path to your local MALLET installation: .../mallet-2.0.8/bin/mallet |
path_to_formatted_training_data | string | Path to where the MALLET formatted training data is stored. |
path_to_model | string | Path to where the model should be stored. |
path_to_topic_key | string | Path to where the topic keys should be stored. |
path_to_topic_distributions | string | Path to where the topic distributions should be stored. |
num_topics | integer | The number of topics to use for training. |

<br> 

### load_topic_keys(*topic_keys_path*)

| Name               | Type              | Description                      |
| ------------------ | ----------------- | -------------------------------- |
| topic_keys_path | string | Path to where the topic keys are stored. |
| RETURNS | list of lists of strings | The 20 most probable words for each topic. |

<br>

### load_topic_distributions(*topic_distributions_path*)

| Name               | Type              | Description                      |
| ------------------ | ----------------- | -------------------------------- |
| topic_distributions_path | string | Path to where the topic distributions are stored. |
| RETURNS | list of lists of integers | Topic distribution (list of probabilities) for each document. |

<br>

### get_top_docs(*training_data, topic_distributions, topic, n=5*)

| Name               | Type              | Description                      |
| ------------------ | ----------------- | -------------------------------- |
| training_data | list of strings | Processed documents that was used to train the topic model. |
| topic_distributions | list of lists of integers | Topic distribution (list of probabilities) for each document. |
| topic | integer | The index of the target topic. |
| n | integer | The number of documents to return. |
| RETURNS | list of tuples (float, string) | The topic probability and document text for the n documents with the highest probability for the target topic. |

<br>

### plot_categories_by_topics_heatmap(*labels, distributions, topics, output_path=None, target_labels=None, dim=None*)
 
| Name               | Type              | Description                      |
| ------------------ | ----------------- | -------------------------------- |
| labels | list of strings | Document labels (e.g., authors of the documents, genres of the documents). |
| distributions | list of lists of integers | Topic distribution (list of probabilities) for each document. |
| topics | list of lists of strings | The 20 most probable words for each topic. |
| output_path | string | Path to where the resulting figure should be saved. |
| target_labels | list of strings | A subset of `labels` to use for plotting. |
| dim | tuple of integers | (x, y) dimensions for the resulting figure. |

<br>

### plot_categories_by_topic_boxplots

<br>

### divide_training_data

<br>

### infer_topics

<br>

### plot_topics_over_time

<br>
