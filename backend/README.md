# Backend - Full Stack Trivia API 

### Installing Dependencies for the Backend

1. **Python 3.7** - Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)


2. **Virtual Enviornment** - We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)


3. **PIP Dependencies** - Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:
```bash
pip install -r requirements.txt
```
This will install all of the required packages we selected within the `requirements.txt` file.


4. **Key Dependencies**
 - [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

 - [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

 - [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server. 

### Database Setup
With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

### Running the server

From within the `./backend` directory first ensure you are working using your created virtual environment.

To run the server, execute:

```bash
python app.py
```

## API Documentation
Below we have separated the documents between the types of expected errors and resource endpoints libraries.

## Errors handlers

```
404
Resource not found
Error type: Server was unable to find what was requested

405
Method not allowed
Error type: Server has rejected the specific method used

422
Unprocessable
Error type: Server was unable to process the contained instructions
```

## Resource Endpoint library

```
Endpoints
GET '/categories'
GET '/categories/{id}/questions'
GET '/questions/?page={int}
POST '/questions'
DELETE '/questions/{id}'
POST '/quizzes'
```

### GET '/categories'
``` 
- Get a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
- Request Argument: None
- Response: An object with a single key, categories, that contains a object of id: category_string key:value pairs. 

{
    '1' : "Science",
    '2' : "Art",
    '3' : "Geography",
    '4' : "History",
    '5' : "Entertainment",
    '6' : "Sports"
}
```

### GET '/categories/{id}/questions'
```
- Get questions for a cateogry specified by id argument
- Request Argument: id -> type: integer
- Response: An object with questions for the specified category, total questions, and current category 

{
    'questions': [
        {
            'id': 20,
            'question': 'What is the heaviest organ in the human body?',
            'answer': 'The Liver', 
            'difficulty': 4,
            'category': 4
        },
    ],
    'total_questions': 4,
    'current_category': 'Science'
}
```

### GET '/questions/?page={int}
```
- Fetches a paginated set of questions, a total number of questions, all categories and current category. 
- Request Argument: page -> type: integer
- Response: An object paginated with 10 questions, total questions, object with all categories and current category.
{
    'questions': [
        {
            'id': 20,
            'question': 'What is the heaviest organ in the human body?',
            'answer': 'The Liver', 
            'difficulty': 4,
            'category': 4
        },
    ],
    'total_questions': 4,
    'categories': { 
    '1' : "Science",
    '2' : "Art",
    '3' : "Geography",
    '4' : "History",
    '5' : "Entertainment",
    '6' : "Sports" 
    },
    'current_category': 'Science'
}
```

### POST '/questions'
```
- Post a request to search for a specific question by search term 
- Request Body: 
{
    'searchTerm': 'search term'
}
- Response: any array of questions, a number of total_questions and the current category
{
    'questions': [
        {
            'id': 20,
            'question': 'What is the heaviest organ in the human body?',
            'answer': 'The Liver', 
            'difficulty': 4,
            'category': 4
        },
    ],
    'total_questions': 4,
    'current_category': 'Science'
}
```

### POST '/questions'
```
- Post a request to add a new question
- Request Body: 
{
    'question':  'Question',
    'answer':  'Answer',
    'difficulty': 5,
    'category': 4,
}
- Response: Nothing (200 Success)
```

### DELETE '/questions/{id}'
```
- Deletes a specified question using the id
- Request Argument: id -> type: integer
- Returns: Nothing (200 Success)
```

### POST '/quizzes'
```
- Post a request to get the next question 
- Request Body: 
{
    'previous_questions': [],
    'quiz_category': 'Science'  
}
- Response: a new question object 
{
    'question': {
        'id': 20,
        'question': 'What is the heaviest organ in the human body?',
        'answer': 'The Liver', 
        'difficulty': 4,
        'category': 4
    }
}
```

## Testing
To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python app_test.py
```
