# Movie Data Importer for DataStax Astra
This script reads movie data from a CSV file and inserts it into a DataStax Astra database in a single table called `movies`. This guide will show you how to set up and run the script using a virtual environment.

## Setup

### Prerequisites
- Python 3.x installed on your system.

- DataStax Astra account and database

- `virtualenv` package installed. You can install it via pip:
  ```
  pip install virtualenv
  ```

### Step 1: Clone the Repository
Clone this repository to your local machine:
  ```bash
  git clone git@github.com:Igor-Britoo/Movie-Data-Importer.git
  cd Movie-Data-Importer
  ```

### Step 2: Create a Virtual Environment

1. **Create a virtual environment**:
  ```bash
  virtualenv venv
  ```

2. **Activate the virtual environment**:
  - **On Windows**:
    ```bash
    venv\Scripts\activate
    ```
  - **On macOS and Linux**:
    ```bash
    source venv/bin/activate
    ```

### Step 3: Install Dependencies
With your virtual environment activated, install the required dependencies:
  ```bash
  pip install -r requirements.txt
  ```

### Step 4: Download Secure Connect Bundle
- Log in to your DataStax Astra account.
- Navigate to your database.
- Go to "Connect" -> "Get a Secure Connect Bundle 🎁" -> "Get Bundle".
- Select the region and click on "Download Secure Bundle".

### Step 5: Generate Client ID and Client Secret
- In your Astra DB dashboard, go to "Connect" -> "Get an application token 🔑" -> "Generate Database Token".
- Generate new client credentials and note down the client ID and client secret.

### Step 6: Create Keyspace and Table
**Create Keyspace and Table Using Astra Web Interface:**
  - In your Astra DB dashboard, go to the "Overview" tab and create the a keyspace named `movies_keyspace`.
  - In the keyspace, create the table `movies` with the following schema:
    ```sql
    CREATE TABLE movie_keyspace.movies (
      director_name TEXT,
      title_year INT,
      movie_title TEXT,
      language TEXT,
      color TEXT,
      num_critic_for_reviews INT,
      duration INT,
      director_facebook_likes INT,
      actor_3_facebook_likes INT,
      actor_2_name TEXT,
      actor_1_facebook_likes INT,
      gross BIGINT,
      genres TEXT,
      actor_1_name TEXT,
      num_voted_users INT,
      cast_total_facebook_likes INT,
      actor_3_name TEXT,
      facenumber_in_poster INT,
      plot_keywords TEXT,
      movie_imdb_link TEXT,
      num_user_for_reviews INT,
      country TEXT,
      content_rating TEXT,
      budget BIGINT,
      actor_2_facebook_likes INT,
      imdb_score FLOAT,
      aspect_ratio FLOAT,
      movie_facebook_likes INT,
      PRIMARY KEY (movie_title)
    );
    ```

## Configuration
**Create a `.env` File**: Create a file named `.env` in the root of your project directory and add your client ID, client secret, and secure connect bundle path:
  ```
  CLIENT_ID=your_client_id
  CLIENT_SECRET=your_client_secret
  SECURE_CONNECT_BUNDLE=path/to/secure-connect-database_name.zip
  ```

## Running the Script
  - **For Mac and Linux:**
    ```
    python3 ./src/movie_data_importer.py
    ```
  - **For Windows:**
    ```
    python ./src/movie_data_importer.py
    ```

The script will read data from the specified CSV file and insert it into the `movies` table in your DataStax Astra database.

## Deactivating the Virtual Environment
After running your script, you can deactivate the virtual environment with:
  ```bash
  deactivate
  ```
This will return you to your system's default Python environment.

### License
This project is licensed under the [MIT License](LICENSE).