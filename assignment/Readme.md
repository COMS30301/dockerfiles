# Docker container for COMS30301 assignments #
Container with [Anaconda Python 2.7](https://hub.docker.com/r/continuumio/anaconda/) and COMS30301 [assignments](https://github.com/coms30301).

## Usage ##
### Python interpreter ###
```
docker run -it coms30301/assignment /bin/bash
```
Finally, go to `/root` where the `spam` directory, containing *spam automarker* is located.

### Python notebook ###
```
docker run -it -p 8888:8888 coms30301/assignment /bin/bash -c "jupyter notebook --notebook-dir=/opt/notebooks --ip='*' --port=8888 --no-browser"
```
Finally, point your browser to [http://localhost:8888](http://localhost:8888) to access the notebooks.

### External storage ###
Any changes made to the files in the Docker image will dissapear once the container is closed. It is possible to work on files from your local drive by using `-v` option with `docker run`.  
For example, if I want to work on a notebook located under `/my/notebooks/example.ipynb` on my local machine I can use `-v /my/notebooks/example.ipynb:/opt/notebooks/assignment_1/example.ipynb` to make it accessible to the Docker image.

## Build ##
```
docker build -t coms30301/assignment .
```
