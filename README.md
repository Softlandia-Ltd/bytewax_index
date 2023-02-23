# Bytewax index

An index to use with Large Language Models (LLMs) to answer questions about
Bytewax documentation and Python API.

## Usage

Make a new virtual env. Then install the requirements

```sh
pip install -r requirements.txt
```

An index-file must exist before you can ask questions. You can run the file
`query_bytewax.py` to create an index, or you can download one
[here](https://drive.google.com/file/d/1YmYX018Hp0G56tnB1vcajpJN-FXUhuOR/view?usp=share_link)

Note that the preloaded index file above only contains a subset of the Bytewax
repository. You can edit the python-file to not exclude any folders. By default,
Rust source files are not included.

Usage requires at least an OpenAI API key in your environment variables. If you
want to recreate the index, a Github API key is needed as well. With the current
configuration, creating an index uses free HuggingFace models, but asking
queries requires OpenAI quota.

To get more relevant answers, increase the `n_sources` parameter (default is 2)

```
python query_bytewax.py -n 3
```

## Example

    Enter query: How can I emit a state after each change or update for a given key
    INFO:root:> [query] Total LLM token usage: 1453 tokens
    INFO:root:> [query] Total embedding token usage: 15 tokens

    To emit a state after each change or update for a given key, you can use a
    stateful map function. This function will take in the key and the new state,
    and then emit the updated state for that key. For example, in the code
    snippet provided, the stateful map function "order_book" is used to update
    the OrderBook object with the new state and then emit the updated state for
    that key. Additionally, the code will check if the order should be removed
    and if not it will update the order. If the order was removed, it will check
    to make sure the bid and ask prices are modified if required. Finally, the
    `capture` operator is used to use the output builder function that was
    defined earlier and print out the output to the terminal.
