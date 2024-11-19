
# Images Lab

---

## Exercise 1: Exploring image creation using single stage build

1. **Run a single stage build:**
   ```bash
   git clone https://github.com/shaibs3/TechTrain_module2.git
   cd ./TechTrain_module2/images
   docker build -f ./singleStagebuild/Dockerfile . -t single_stage_image
   ```

2. **Create a container from the image and test it is running by using the browser:**
   ```bash
   docker run -p 4000:3000 -d single_stage_image
   curl http://localhost:4000
   ```
3. **Find the image size**
   ```bash
   < find the docker command that gets the image size >
   ```
---

## Exercise 2: Exploring image creation using a multy stage build

1. **Run a single stage build:**
   ```bash
   cd ./images
   docker build -f ./multyStagebuild/Dockerfile . -t multy_stage_image
   ```

2. **Create a container from the image and test it is running by using the browser:**
   ```bash
   docker run -p 5000:3000 -d multy_stage_image
   curl http://localhost:5000
   ```
3. **Find the image size**
4. **Question** Was there a diff? Why?

---

## Exercise 3: optimizing image size
1. Try to optimize the image size from exercise 2 by using a slim version of node image. Do the relevant change in the Dockerfile
2. Build the new image and tag it with a slim suffix. i.e **docker build -f ./multyStagebuild/Dockerfile . -t multy_stage_image_slim**
3. **Question** How much improvement did you get?
4. Do the same steps for distroless image.
5. **Question** How much improvement did you get now?
