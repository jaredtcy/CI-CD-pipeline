

<!-- ABOUT THE PROJECT -->
## Project Description

This project involves the process of creating a CI/CD pipeline to identify new commits on "release"/"staging" branch and these actions will be performed:
1. Build/Test using [node.js.yml workflow](https://github.com/jaredtcy/Task-2/blob/master/.github/workflows/node.js.yml)
2. Containerising and deploying the application on AWS ECS using [aws.yml workflow](https://github.com/jaredtcy/Task-2/blob/master/.github/workflows/aws.yml)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started

1. Perform a clone of this github repository to your desktop

  ```sh
  $ git clone --bare https://github.com/jaredtcy/Task-2
  ```
2. Navigate to the directory where the file is being stored at 
  ```sh
  cd Task-2
  ```
3. Verify that the app is working
  ```sh
  npm install express
  ```
  ```sh
  node index.js
  ```
4. Go to your browser to access the webpage [localhost:3000](http://localhost:3000/) which should look like:

(For the "Release" Branch):
![Screenshot 2021-12-12 at 2 11 45 PM](https://user-images.githubusercontent.com/83501266/145705615-57d41a1c-f163-4b8c-9976-a15dea3af713.png)

(For the "Staging" Branch):
![Screenshot 2021-12-12 at 2 39 19 PM](https://user-images.githubusercontent.com/83501266/145705706-7f6409fd-ccdf-40e8-89f2-87cd60a21376.png)

5. Perform a Git push of the files to your local Github repository
  ```sh
  git push https://github.com/<Username>/<Location of file to store in>
  ```

Note: 
-Changes on the "Release" Branch can be made in the questionRepository.js file [here](https://github.com/jaredtcy/Task-2/blob/release/models/questionRepository.js)
-Changes on the "Staging" Branch can be made in the questionRepository.js file [here](https://github.com/jaredtcy/Task-2/blob/staging/models/questionRepository.js)


<p align="right">(<a href="#top">back to top</a>)</p>

## Commiting a change to either the "Release"/"Staging" Branch  

1. Access the "Release"/"Staging" Branch, perform an edit on any files and commit the change
2. Observe the Actions being triggered in the "Actions" Tab (Located in the homepage if your project)
![Screenshot 2021-12-12 at 4 37 16 PM](https://user-images.githubusercontent.com/83501266/145705877-abe6d772-a027-4945-b7d7-6eed832710c2.png)

<p align="right">(<a href="#top">back to top</a>)</p>

## Perform a release of the changes that has been made to the production environment and deploy it to Amazon ECS

1. Access "Releases" (Located in the homepage of your project)
2. Tag your release (E.g. v0.01) for easy identification purpose
3. Publish release
4. Navigate to "Action Tab" and see that the "Deploy to Amazon ECS" action is being executed
![Screenshot 2021-12-12 at 4 43 54 PM](https://user-images.githubusercontent.com/83501266/145706017-672e7fdb-65c4-4ac3-b569-b08a947243b3.png)


<p align="right">(<a href="#top">back to top</a>)</p>


