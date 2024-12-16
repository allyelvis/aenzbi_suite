Here’s a README.md file that you can use for the Aenzbi Suite project. It includes instructions on how to set up and run the project, as well as an overview of the structure and functionality.


---

Aenzbi Suite

Aenzbi Suite is a comprehensive business management platform featuring a Django backend, RESTful APIs, and a modular frontend. The suite includes various applications for eCommerce, POS, Finance, Marketing, Hospitality, Retail, and Entertainment, all integrated under a unified platform. This README provides setup instructions and usage details.


---

Table of Contents

1. Project Overview


2. Getting Started


3. Project Structure


4. Running the Project


5. Docker Setup


6. Frontend Setup


7. Backend Setup


8. Sample Data


9. API Endpoints


10. Contributing




---

Project Overview

Aenzbi Suite is designed to streamline business operations across multiple domains such as retail, hospitality, and finance. It includes both backend APIs for data handling and a frontend for visualization and interaction with business data.


---

Getting Started

To get started with Aenzbi Suite, you’ll need to clone the repository and follow the instructions to set up the backend and frontend.

1. Clone the repository:

git clone https://github.com/yourusername/aenzbi-suite.git
cd aenzbi-suite


2. Make sure Docker is installed on your system for containerized deployment (recommended).




---

Project Structure

Aenzbi Suite
│
├── backend/                 # Django backend with API endpoints
│   ├── ecommerce/           # eCommerce application
│   ├── pos/                 # Point-of-sale application
│   ├── finance/             # Finance application
│   ├── marketing/           # Marketing application
│   ├── hospitality/         # Hospitality application
│   ├── retail/              # Retail application
│   └── entertainment/       # Entertainment application
│
├── frontend/                # Modular HTML frontend with eCommerce and other modules
│   ├── index.html           # Home page
│   ├── modules/             # Various business modules
│   └── assets/              # Static files (CSS, JS, images)
│
├── Dockerfile               # Docker configuration for backend
├── docker-compose.yml       # Docker Compose configuration
├── requirements.txt         # Python dependencies
└── setup_aenzbi_suite.sh    # Bash script to automate setup


---

Running the Project

Step 1: Install dependencies

Before running the project, ensure you have Python 3.x and Docker installed. If you are using the Bash script, it will automate the setup process for you.

1. Install dependencies for the backend:

python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt


2. For frontend, you don't need to install additional dependencies manually if you are using Docker.



Step 2: Run the project

You can run the entire project using Docker Compose.

1. To build and start the containers, run:

./setup_aenzbi_suite.sh

This will:

Build the backend container (Django API)

Build the frontend container (Nginx serving static HTML)

Set up the database and migrate

Load sample data into the database



2. Once the setup is complete, the project will be available at the following URLs:

Backend (API): http://127.0.0.1:8000/api/ecommerce/products/

Frontend: http://127.0.0.1:8080/modules/ecommerce.html





---

Docker Setup

This project uses Docker to containerize both the backend (Django) and frontend (static HTML served via Nginx). Docker Compose is used to orchestrate the services.

1. Build and run Docker containers:

docker-compose build
docker-compose up -d


2. Stopping the containers:

docker-compose down




---

Frontend Setup

The frontend is built using static HTML, CSS, and JavaScript. It fetches data from the Django API to display products and other business-related data.

1. You can find the HTML templates in the frontend/ directory. Each business module has a corresponding HTML file under frontend/modules/.


2. The eCommerce module demonstrates fetching product data from the API:

fetch("http://127.0.0.1:8000/api/ecommerce/products/")
    .then(response => response.json())
    .then(data => {
        const productList = document.getElementById('product-list');
        data.forEach(product => {
            const productItem = document.createElement('div');
            productItem.innerHTML = \`
                <h3>\${product.name}</h3>
                <p>\${product.description}</p>
                <p>Price: \$\${product.price}</p>
                <img src="\${product.image_url}" alt="\${product.name}">
            \`;
            productList.appendChild(productItem);
        });
    });




---

Backend Setup

The backend is built using Django, with REST API endpoints for each business module.

1. The Django backend is initialized in the backend/ directory. It includes apps like ecommerce, pos, finance, and more.


2. Run the migrations to set up the database:

python manage.py migrate


3. Load sample data into the database:

python manage.py loaddata ecommerce/fixtures/sample_data.json


4. Start the backend server:

python manage.py runserver




---

Sample Data

Sample data for the eCommerce module is provided in ecommerce/fixtures/sample_data.json. The script automatically loads this data into the database during setup.


---

API Endpoints

Here are the primary API endpoints available:

eCommerce API:

GET /api/ecommerce/products/: Lists all products



You can extend the backend with additional API endpoints for other modules (POS, Finance, etc.).


---

Contributing

We welcome contributions to the Aenzbi Suite project. If you have suggestions or find bugs, feel free to open an issue or submit a pull request.


---

License

This project is licensed under the MIT License - see the LICENSE file for details.


---

This README.md provides a clear and concise guide for setting up and using the Aenzbi Suite project.©AENZBi