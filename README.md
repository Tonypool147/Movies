An API that allows users to query and consume values from a SQL database - provided by MoviesDB.bak and transalated from a csv file .
from the dataset at: https://www.kaggle.com/datasets/disham993/9000-movies-dataset

I have concentrated on creating a good APi rather than creating UI's for the results.

The datastore for the app is a SQL database - which can be created by restoring the sql backup file MoviesDB.bak 
It was transalated from the csv file provided by the dataset at: https://www.kaggle.com/datasets/disham993/9000-movies-dataset

The API uses Entity Framework for mapping the underlaying data to the application Entities 

Testing was carried out using Postman. Swagger has been incorporoated so you can see the API methods in details via the browser
**[https://localhost:7266/swagger]**

I have use Log4net for server-side logging. This is highly effective and easy to use and is the 
logging system of choice for my current workplace.

For some api calls I have used a different data model than the server side model to return the data as might be the case
in a real world environment where not all the information would or should be required by the caller. 
These models are under the DTO folder.

Paging has been added to some api calls where appropriate - when large resultsets are expected,
It is an optional paging feature -simply add Page=<..> and PagsSize=<..> as parameters when paging is required.

In a live environment the project would have some sort of authentication and/or authorisation
but I have left it out here for simplicity and ease of use.

Examples for each of the api calls is below:
Note: SortBy is currently restricted to either 'Title' or 'Release_date'

**Search Movie By title**
https://localhost:7266/api/Movie/Search?title=batman&sortBy=release_date    [sortBy=optional]
**Search Movie By Details**
https://localhost:7266/api/Movie/Search?details=batman&sortBy=release_date  [sortBy=optional]
**Search Movie by Id (one returned)**
https://localhost:7266/api/Movie/5                                   
**Search movies By Genre**
https://localhost:7266/api/Movie/SearchByGenre/Crime?PageSize=50&sortBy=release_date  [Page,PageSize,sortBy = optional]
**Search movies By Actor**
https://localhost:7266/api/Movie/SearchByActor/Niro?Page=7&Pagesize=1000&sortBy=title    [Page,PageSize,sortBy = optional]
**Top 100 Movies By Vote**
https://localhost:7266/api/Movie/Top100ByVote?Genre=Action   		    [Genre=optional]
**Top 100 movies By Popularity**
https://localhost:7266/api/Movie/Top100ByPopularity
