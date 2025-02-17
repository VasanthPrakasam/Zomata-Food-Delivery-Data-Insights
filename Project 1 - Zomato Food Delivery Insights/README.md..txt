# Zomato Food Delivery Data Insights

## Project Description

This project develops an interactive Streamlit application for analyzing and gaining insights from food delivery data. The application is designed for a fictional food delivery company, Zomato. It facilitates data entry, management, and visualization to understand key operational aspects, customer behavior, and delivery performance. The project utilizes Python, MySQL, and Streamlit to provide a user-friendly interface for data exploration and analysis.

## Setup and Running the Project

### Prerequisites

*   Python 3.7 or higher
*   Git (for version control and cloning the repository)
*   MySQL database server
*   A modern web browser (Chrome, Firefox, Safari, etc.)

### Installation

1.  **Clone the repository:**

    ```bash
    git clone <your_github_repo_url>
    cd Zomata-Food-Delivery-Data-Insights
    ```

    (Replace `<your_github_repo_url>` with the actual URL of your GitHub repository.)

2.  **Create a virtual environment (recommended):**

    ```bash
    python -m venv .venv
    .venv\Scripts\activate  # For Windows
    source .venv/bin/activate # For Linux/macOS
    ```

3.  **Configure MySQL database:**

    *   Create a MySQL database (e.g., `zomato`).
    *   Update the database connection details in your Streamlit app (likely in a file like `src/streamlit_app.py` or in a configuration file) to match your MySQL server's host, username, password, and database name. You will likely need to install the appropriate MySQL connector for Python (e.g., `mysql-connector-python`): `pip install mysql-connector-python`
4.  **Install the required Python packages:**

    ```bash
    pip install -r requirements.txt
    ```

### Running the Application

1.  **Run the Streamlit app:**

    ```bash
    streamlit run src/streamlit_app.py
    ```

    This command will launch the Streamlit application in your default web browser. It will likely open automatically, but if not, look for a message in the terminal that shows the URL (usually something like `http://localhost:8501`).

2.  **To run the data analysis app:**

    ```bash
    streamlit run src/data_analysis.py
    ```

## How to Use the Application

### Main Streamlit App (src/streamlit_app.py)

*   **Data Display:** This app displays the content of the 'orders' table.
*   **Refresh Button:** The "Refresh Data" button reloads the data from the MySQL database.
*   **Future Enhancements:** This app can be extended to include:
    *   Data entry forms for adding, updating, and deleting records across all tables (Customers, Restaurants, Orders, Deliveries).
    *   Dynamic table creation and modification capabilities.
    *   More comprehensive data visualization.
    *   Improved error handling and user feedback.

### Data Analysis App (src/data_analysis.py)

*   **Data Analysis Tab:** This app performs and displays some basic data analysis queries.
*   **Orders by Date:** Displays a count of orders placed on each date.
*   **Orders by Status:** Shows the number of orders in each status (e.g., 'Pending', 'Delivered', 'Cancelled').
*   **Orders by Customer:** Lists the number of orders placed by each customer.
*   **Future Enhancements:**
    *   Implement more complex SQL queries to extract and visualize various data insights.
    *   Add interactive charts and graphs using libraries like `matplotlib` or `plotly`.
    *   Implement filtering and sorting capabilities.
    *   Integrate with other data sources (e.g., APIs) to provide richer data.

## Data Information

### Data Source

The data used in this project is a synthetic dataset generated using the Faker Python library. The data is stored in a MySQL database and is initially populated by CSV files (`data/customers.csv`, `data/orders.csv`, `data/restaurants.csv`, and `data/deliveries.csv`).

### Data Schema

The data is organized into four main tables:

1.  **Customers Table:** Stores customer information.

    *   `customer_id` (INT, PRIMARY KEY): Unique identifier for each customer.
    *   `name` (VARCHAR(255)): Customer's full name.
    *   `email` (VARCHAR(255)): Contact email address.
    *   `phone` (VARCHAR(20)): Contact phone number.
    *   `location` (VARCHAR(255)): Customer's address.
    *   `signup_date` (DATE): Date the customer signed up.
    *   `is_premium` (BOOLEAN): Indicates if the customer has a premium membership.
    *   `preferred_cuisine` (VARCHAR(255)): Customer's preferred cuisine.
    *   `total_orders` (INT): Total number of orders placed.
    *   `average_rating` (DECIMAL(3,2)): Average rating given to restaurants.

2.  **Restaurants Table:** Stores restaurant information.

    *   `restaurant_id` (INT, PRIMARY KEY): Unique identifier for each restaurant.
    *   `name` (VARCHAR(255)): Restaurant name.
    *   `cuisine_type` (VARCHAR(255)): Primary cuisine type.
    *   `location` (VARCHAR(255)): Restaurant location.
    *   `owner_name` (VARCHAR(255)): Name of the restaurant owner.
    *   `average_delivery_time` (DECIMAL(5,2)): Average delivery time (in minutes).
    *   `contact_number` (VARCHAR(20)): Restaurant's contact number.
    *   `rating` (DECIMAL(3,2)): Average customer rating (1-5 scale).
    *   `total_orders` (INT): Total orders received.
    *   `is_active` (BOOLEAN): Indicates if the restaurant is active.

3.  **Orders Table:** Manages order details.

    *   `order_id` (INT, PRIMARY KEY): Unique identifier for each order.
    *   `customer_id` (INT): Foreign key referencing `customer_id` in `Customers`.
    *   `restaurant_id` (INT): Foreign key referencing `restaurant_id` in `Restaurants`.
    *   `order_date` (DATETIME): Date and time when the order was placed.
    *   `delivery_time` (DATETIME): Date and time the order was delivered.
    *   `status` (VARCHAR(50)): Order status (e.g., 'Pending', 'Delivered', 'Cancelled').
    *   `total_amount` (DECIMAL(10,2)): Total bill amount.
    *   `payment_mode` (VARCHAR(50)): Payment mode used.
    *   `discount_applied` (DECIMAL(10,2)): Discount amount applied.
    *   `feedback_rating` (DECIMAL(3,2)): Rating given by the customer.

4.  **Deliveries Table:** Stores delivery information.

    *   `delivery_id` (INT, PRIMARY KEY): Unique identifier for each delivery.
    *   `order_id` (INT): Foreign key referencing `order_id` in `Orders`.
    *   `delivery_person_id` (INT): (Not used in current version of the project).
    *   `delivery_status` (VARCHAR(50)): Current delivery status (e.g., 'On the way', 'Delivered').
    *   `distance` (DECIMAL(10,2)): Distance of delivery (in kilometers).
    *   `delivery_time` (DECIMAL(5,2)): Actual time taken for delivery (in minutes).
    *   `estimated_time` (DECIMAL(5,2)): Estimated delivery time (in minutes).
    *   `delivery_fee` (DECIMAL(10,2)): Delivery fee charged.
    *   `vehicle_type` (VARCHAR(50)): Type of vehicle used.

