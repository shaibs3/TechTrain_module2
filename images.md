
# Images Lab

---
## Exercise 1: Exploring image creation and caching

1. **Run a single stage build:**
   ```bash
   git clone https://github.com/shaibs3/TechTrain_module2.git
   cd ./TechTrain_module2/imageCaching
   ```

2. **Build the container and Observe the output.Each RUN, COPY, and other command in the Dockerfile corresponds to a separate layer:**
   ```bash
    docker build -t caching-demo:1.0 .  
   ```
3. **Rebuild the Image Without Changes**
   ```bash
   docker build -t caching-demo:1.0 .
   ```
4. **Observe the output this time. You will see that Docker uses cached layers for all steps.**
5. **Modify the sample.txt File. Do a small change to the file**
    ```bash
    echo "This file has been updated!" > sample.txt
    ```
6. **Rebuild the image**
   ```bash
   docker build -t caching-demo:1.0 .
   ```
7. Observe the output. **Question** why is the output has changed compared to the output in step 4

8. Add any kind of package install to the Dockerfile right after the RUN apt-get update command. i.e
   ```bash
   apt install -y tcpdump
   ```
9. **Rebuild the image**
   ```bash
   docker build -t caching-demo:1.0 .
      ```
7. Observe the output. **Question** how many layers were taken from cache this time?

---
## Exercise 2: Exploring image creation using single stage build

1. **Run a single stage build:**
   ```bash
   cd ./TechTrain_module2/images
   docker build -f ./singleStagebuild/Dockerfile . -t single_stage_image
   ```

2. **Create a container from the image and test it is running by using the browser:**
   ```bash
   docker run -p 4000:3000 --name single_stage_container -d single_stage_image
   sleep 1
   curl http://localhost:4000
   ```
3. **Find the image size**
   ```bash
   < find the docker command that gets the image size >
   ```
---

## Exercise 3: Exploring image creation using a multy stage build

1. **Run a single stage build:**
   ```bash
   cd ./images
   docker build -f ./multyStagebuild/Dockerfile . -t multy_stage_image
   ```

2. **Create a container from the image and test it is running by using the browser:**
   ```bash
   docker run -p 5000:3000 --name multy_stage_container -d multy_stage_image
   sleep 1
   curl http://localhost:5000
   ```
3. **Find the image size**
4. **Question** Was there a diff? Why?

---

## Exercise 4: optimizing image size
1. Try to optimize the image size from exercise 2 by using a slim version of node image. Do the relevant change in the Dockerfile
2. Build the new image and tag it with a slim suffix. i.e **docker build -f ./multyStagebuild/Dockerfile . -t multy_stage_image_slim**
3. **Question** How much improvement did you get?
4. Do the same steps for a distroless image.
5. **Question** How much improvement did you get now?
