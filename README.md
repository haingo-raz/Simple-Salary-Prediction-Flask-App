# About
This project is a basic Flask application containerized using Docker. It features a simple linear regression model trained to predict salaries based on years of experience. The model has been trained on a very small [dataset](https://www.kaggle.com/datasets/karthickveerakumar/salary-data-simple-linear-regression) and does not reflect the realities of salary against experience. This project is only a proof of concept and serves as training for using Docker. The model is integrated into the Flask app, allowing users to input their years of experience and receive a predicted salary.

# How to Run the App
To run the app locally, follow these steps"
1. Open your terminal and navigate to the project directory.

1. Run the following command to build and start the Docker container: `docker-compose up --build`. 

1. Once the container is running, the app will be accessible on port 5000 of your local machine. Open your browser and go to: http://localhost:5000 to view the site. 

# Deploying to EC2
The following steps are applicable if your local machine has the same CPU architecture as the EC2 instance (x86 or ARM):

1. Build the Docker image locally by running the following command from the project directory:: `docker build -t ec2-flask-demo:v1.0 .`

1. Save the Docker image as a tarball to compress the artifact before uploading it to the EC2 instance:: `docker save -o ec2-flask-demo.tar ec2-flask-demo:v1.0`

You should now see a .tar file in the project directory.

1. Upload the tar file to the EC2 instance using scp: `scp -i vs-kp-1.pem ec2-flask-demo.tar ec2-user@3.142.211.164:/home/ec2-user/docker_images`

1. If you encounter a permissions error with the .pem file, set the correct permissions by running:: `chmod 600 vs-kp-1.pem`

1. The size of the Docker image tar file is 162 MB. Once uploaded, you can verify its presence by running ls within the EC2 instance.