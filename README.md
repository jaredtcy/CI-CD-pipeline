

<!-- ABOUT THE PROJECT -->
## Project Description

This project involves the process of creating a CI/CD pipeline to identify new commits on "release"/"staging" branch and these actions will be performed:
1. Build/Test using [node.js.yml workflow](https://github.com/jaredtcy/Task-2/blob/master/.github/workflows/node.js.yml)
2. Containerising and deploying the application on AWS ECS using [aws.yml workflow](https://github.com/jaredtcy/Task-2/blob/master/.github/workflows/aws.yml)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started

**1. Perform a clone of this github repository to your desktop**

  ```sh
  $ git clone --bare https://github.com/jaredtcy/Task-2
  ```
**2. Navigate to the directory where the file is being stored at** 
  ```sh
  cd desktop
  ```
**3. Verify that the app is working**
  ```sh
  npm install express
  ```
  ```sh
  node index.js
  ```
**4. Go to your browser to access the webpage [localhost:3000](http://localhost:3000/) which should look like:**

(For the "Release" Branch):
![Screenshot 2021-12-12 at 2 11 45 PM](https://user-images.githubusercontent.com/83501266/145705615-57d41a1c-f163-4b8c-9976-a15dea3af713.png)
Changes on the "Release" Branch can be made in the questionRepository.js file [here](https://github.com/jaredtcy/Task-2/blob/release/models/questionRepository.js)

(For the "Staging" Branch):
![Screenshot 2021-12-12 at 2 39 19 PM](https://user-images.githubusercontent.com/83501266/145705706-7f6409fd-ccdf-40e8-89f2-87cd60a21376.png)
Changes on the "Staging" Branch can be made in the questionRepository.js file [here](https://github.com/jaredtcy/Task-2/blob/staging/models/questionRepository.js)

**5. Perform a Git push of the files to your local Github repository**
  ```sh
  git push https://github.com/<Username>/<Location of file to store in>
  ```


**6. Setting up Amazon ECS**

- Creating a new Repository in ECS
- Create a Task in ECS (Under Task Definitions)
  - Choose Instance Type as Fargate
  - Select Role as ecsTaskExecutionRole
- Add a container with port mapping 3000 <Can add any desired port here>
- Under task->Volumes, select "Configure Via JSON"
- Paste the JSON code into a new file named [task-definition](https://github.com/jaredtcy/Task-2/blob/master/task-definition.json)
- Create a new Target Group
- Create a Load Balancer
- Create a new Cluster in ECS
- Create a new Service to Connect them
  - Ensure that Target Group and Load Balancer is being selected as the option when configuring

**7. Add a GitHub Action**
- For the Deployment of the Application on ECS
  - Navigate to "Actions" tab from the main page
  - Select "Deploy to Amazon ECS", similar to [aws.yml workflow](https://github.com/jaredtcy/Task-2/blob/master/.github/workflows/aws.yml)
  
- For Building/Testing the Application 
  - Navigate to "Actions" tab from the main page
  - Select "Deploy to Amazon ECS", similar to [node.js.yml workflow](https://github.com/jaredtcy/Task-2/blob/master/.github/workflows/node.js.yml)





<p align="right">(<a href="#top">back to top</a>)</p>

## Commiting a change to either the "Release"/"Staging" Branch  

1. Access the "Release"/"Staging" Branch, perform an edit on any files and commit the change
2. Observe the Actions being triggered in the "Actions" Tab (Located in the homepage if your project)
![Screenshot 2021-12-12 at 4 37 16 PM](https://user-images.githubusercontent.com/83501266/145705877-abe6d772-a027-4945-b7d7-6eed832710c2.png)
3. Current workflow is configured to stop when any task fails. This can be edited accordingly in the node.js.yml file
  ```sh
  continue-on-error: false
  ```
  
  

<p align="right">(<a href="#top">back to top</a>)</p>

## Perform a release of the changes that has been made to the production environment and deploy it to Amazon ECS

1. Access "Releases" (Located in the homepage of your project)
2. Tag your release (E.g. v0.01) for easy identification purpose
3. Select "Publish Release" to release the changes to the Production Environment
4. Navigate to "Action Tab" and see that the "Deploy to Amazon ECS" action is being executed
![Screenshot 2021-12-12 at 4 43 54 PM](https://user-images.githubusercontent.com/83501266/145706017-672e7fdb-65c4-4ac3-b569-b08a947243b3.png)
5. Current workflow is configured to stop when any task fails. This can be edited accordingly in the aws.yml file.
  ```sh
  continue-on-error: false
  ```


<p align="right">(<a href="#top">back to top</a>)</p>


## Configuring automated email to be sent out when a job fails
  
1. From [aws.yml workflow](https://github.com/jaredtcy/Task-2/blob/master/.github/workflows/aws.yml) as well as [node.js.yml workflow](https://github.com/jaredtcy/Task-2/blob/master/.github/workflows/node.js.yml), a snippet of code has been added at the bottom to automate this email sending
   ```sh
      - name: Send mail
      if: ${{ failure() }}
      uses: dawidd6/action-send-mail@v3
      with:
      # Required mail server address:
        server_address: smtp.gmail.com
      # Required mail server port:
        server_port: 465
      # Optional (recommended): mail server username:
        username: ${{secrets.MAIL_USERNAME}}
      # Optional (recommended) mail server password:
        password: ${{secrets.MAIL_PASSWORD}}
      # Required mail subject:
        subject: Github Actions job result
      # Required recipients' addresses:
        to: testing@example.com,test@example.com
      # Required sender full name (address can be skipped):
        from: Jared Tan # <user@example.com>
    ```
 2. For this project, Gmail is used for the automated sending of email. For more information on how we can configure Gmail settings to enable the sending of email, please refer to this [Documentation](https://github.com/dawidd6/action-send-mail)

  
<p align="right">(<a href="#top">back to top</a>)</p>

