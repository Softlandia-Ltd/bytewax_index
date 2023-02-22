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
