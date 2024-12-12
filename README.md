# employee-management
employee management system

The Project is build in laravel framework

-------Go inside the project folder (example-app) and run the following to get the vendor folder---------------
-composer dump-autoload
-composer install

URL of the project : http://127.0.0.1:8000/api/employee/list  

---- MySQL connect string (inside .evn file)----------
DB_CONNECTION=mysql
DB_HOST=127.0.0.1    
DB_PORT=3306        //port number
DB_DATABASE=employee_db  //name of the database
DB_USERNAME=root  //database user
DB_PASSWORD=      //no password

-------------List of all available routes in the project and are tested via Postman ------------------

//import employee csv route   =>     (Postman URL = http://127.0.0.1:8000/api/employee    form-data: csv_file)
Route::post('employee', [EmployeeController::class, 'import']);

//list all the employees (with default pagination limit as 100)  => (Postman URL = http://127.0.0.1:8000/api/employee/list)
Route::get('employee/list', [EmployeeController::class, 'index']);

//find an employee with id    => (Postman URL = http://127.0.0.1:8000/api/employee/{emp_id})
Route::get('employee/{id}', [EmployeeController::class, 'show']);

//delete an employee with id => (Postman URL = http://127.0.0.1:8000/api/employee/{emp_id})
Route::post('employee/{id}', [EmployeeController::class, 'destroy']);


//serve the error log files (this file will show all the errors which encountered while importing the csv file)           => http://127.0.0.1:8000/api/logs-files/csv_import_errors-{todays-day in yyyy-mm-dd}.log
Route::get('logs-files/{filename}', [EmployeeController::class, 'logsFiles']);




------------------ Following libraries has been installed via composer----------------
composer require league/csv


------------- Some possible improvement in the current code -------------------------
1. Some additional check for input validations in the backend code
2. Customized error messages to the users.
3. Make the import csv job as independent process and inform the user via email once the csv is processed (i.e. User don't need to wait on the screen for the entire file to process, he/she just need to wait till the file processing starts)

