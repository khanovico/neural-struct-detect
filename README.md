# Deep Nerual Network approach for Sturcture Detection

## Setup

The software is ready for Docker: the image can be created from `Dockerfile` by running `docker build -t deeplytough .` (image size ~4.7GB so you may have to increase the disk space available to docker). The DeeplyTough tool is then accessible
conda environment inside the container with `source activate deeplytough`.

```bash
# create new python 3 env and activate
conda create -y -n deeplytough python=3.6
# create python2 env used for protein structure preprocessing
conda create -y -n deeplytough_mgltools python=2.7
conda install -y -n deeplytough_mgltools -c bioconda mgltools=1.5.6
```
### Environment setup

To run the evaluation and training scripts, please first set the `DEEPLYTOUGH` environment variable to the directory containing this repository and then update the `PYTHONPATH` and `PATH` variables respectively:
```bash
export DEEPLYTOUGH=/path_to_this_repository
export PYTHONPATH=$DEEPLYTOUGH/deeplytough:$PYTHONPATH
export PATH=$DEEPLYTOUGH/fpocket2/bin:$PATH
```

## Training

Training requires a GPU with >=11GB of memory and takes about 1.5 days on recent hardware. In addition, at least a 4-core CPU is recommended due to volumetric input pre-processing being an expensive task.

Note that due to non-determinism inherent to the currently established process of training deep networks, it is nearly impossible to exactly reproduce the pre-trained networks in `networks` directory.

Also note the convenience of an output directory containing "TTTT" will afford this substring being replaced by the current `datetime`.
