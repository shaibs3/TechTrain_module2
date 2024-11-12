
# Images Lab

---

## Exercise 1: Exploring image creation using single stage build

1. **Run a single stage build:**
   ```bash
   cd ./images
   docker build -f ./singleStagebuild/Dockerfile . -t single_stage_image
   ```

2. **Create a container from the image and test it is running by using the browser:**
   ```bash
   http://localhost:3000
   ```
3. **Find the image size**

---

## Exercise 2: Exploring image creation using multy stage build

1. **Run a single stage build:**
   ```bash
   cd ./images
   docker build -f ./multyStagebuild/Dockerfile . -t multy_stage_image
   ```

2. **Create a container from the image and test it is running by using the browser:**
   ```bash
   http://localhost:3000
   ```
3. **Find the image size**
4. **Question** Was there a diff? Why?

---

## Exercise 3: optimizing image size
1. Try to optimize the image size from exercise 2 by using a slim version of node image
2. Build the new image
3. **Question** How much improvement did you get?
4. Do the same steps for distroless image.
5. **Question** How much improvement did you get now?
