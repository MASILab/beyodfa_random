# Beyond FA Random

Here is an example repository for the Beyond FA challenge. This docker generates 128 random features in the range of [0,1] for testing.

## Building the Docker

See `Dockerfile` for an example of setting up the Docker container. 

To build this Docker container, clone the repository and run the following command in the root directory:

```bash
DOCKER_BUILDKIT=1 sudo docker build -t beyondfa_random:v1.0.1 .
```

The Docker runs the code from `scripts/entrypoint.sh`.

## Running the Docker

Your Docker container should be able to read input data from `/input` and write output data to `/output`. Honestly, it does not read anything, just writes. 
**The JSON list contains 128 values.**

To run this Docker:

```bash
input_dir=".../input_data"
output_dir=".../output_data"

mkdir -p $output_dir
sudo chmod 777 $output_dir

sudo docker run --rm\
    -e METRIC=random_features \
    -v $input_dir:/input \
    -v $output_dir:/output \
    beyondfa_random:v1.0.1
```
