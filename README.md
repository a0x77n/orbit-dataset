# Dataset for Research Project "Orbit"

This repository contains all the data used in the evaluation of the research paper ["On the Role of Pre-trained Embeddings in Binary Code Analysis"](https://mlsec.org/docs/2024a-asiaccs.pdf) published in the Proceedings of the 19th ACM Asia Conference on Computer and Communications Security.

## Raw Debian Packages

The [`debs`](./debs) directory contains the raw Debian packages used in our evaluation. Multiple compilation configurations exist for each source package, and depending on the source package, multiple binary packages may be generated.

The directory structure is as follows: `./debs/<source_pkg>/<compilation_id>/<binary_pkg>.deb`.

## JSON Dump

The [`fundump`](./fundump) directory contains a JSON file for each binary package from the `debs` directory, including data and labels for each function extracted from the package. It also contains additional metadata.

Each file consists of a list of JSON objects representing a function. Below is an example structure:

```json
{
    "src_deb": "...",
    "deb": "...",
    "version": "...",
    "arch": "...",
    "producer": "...",
    "optimization_option": "...",
    "compiler": "...",
    "binary": "...",
    "function": "...",
    "full_path": "...",
    "line": "...",
    "column": "...",
    "bytes": "...",
    "addr": "...",
    "signature": {
        "return_type": "...",
        "parameter_list": [
            {
                "index": 1,
                "name": "...",
                "type": "..."
            },
            {
                "index": 2,
                "name": "...",
                "type": "..."
            }
        ]
    }
}
```

The directory structure is as follows: `./fundump/<source_pkg>/<compilation_id>/<binary_pkg>.json.xz`.

## Function Similarity Dataset

The directory [`function-similarity`](./function-similarity) contains the JSON files [`train-data.json.xz`](./function-similarity/train-data.json.xz) and [`test-data.json.xz`](./function-similarity/test-data.json.xz) with the training and test data, respectively, for the function similarity experiments.

Each file consists of a list of labeled function pairs. An example structure is shown below:

```json
{
    "function1": {
        "bytes": "...",
        "addr": "..."
    },
    "function2": {
        "bytes": "...",
        "addr": "..."
    },
    "label": "..."
}
```

## Cloning the Repository with Git LFS

This repository uses Git LFS (Large File Storage) to manage the dataset files. To ensure that you properly clone all the large files along with the rest of the repository, please make sure you have Git LFS installed.

## Contact

For any inquiries, please contact Alwin Maier at [mlsec-alwin@posteo.de](mailto:mlsec-alwin@posteo.de).
