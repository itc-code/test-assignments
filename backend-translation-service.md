# Translation Service Challenge
## Goal
The goal of this challenge is to create a microservice providing an API to work with word
definitions/translations taken from Google Translate. Note that support of anything longer than a single
word is not required.
## Endpoints
* Get the details about the given word.

The response shall include definitions, synonyms, translations and examples taken from the corresponding Google Translate page (e.g. [challenge word translation](https://translate.google.com/?sl=en&tl=ru&text=challenge&op=translate)).

Data fetched from Google Translate has to be saved in the DB. When a request arrives to the endpoint, the handler has to look for the word in the DB first and fall back to Google Translate only if it is not there.

* Get the list of the words stored in the database.

Pagination, sorting and filtering by word is required. Partial match has to be used for filtering.
Definitions, synonyms and translations shall not be included in the response by default but can be enabled by providing corresponding query parameters.
* Delete a word from the database.
## Non functional requirements
* ```Python 3.10``` and ```FastAPI``` web framework have to be used. All other libraries are up to the candidate.
* ```Dockerfile``` and ```docker-compose.yml``` have to be included.
* Database choice is up to the candidate.
* The microservice has to be production ready (interpretation of this is up to the candidate).
## Other
If the final solution is not ideal, please, provide the document with a brief description of the known flaws and
possible ways of improvement. Any other clarifications and comments may also be included.