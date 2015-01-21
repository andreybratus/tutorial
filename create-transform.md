# Tutorial to create a simple transform with OpenRefine

Requirements for this tutorial:

* Install **OpenRefine** from [here](http://openrefine.org) or form [git](https://github.com/OpenRefine/OpenRefine.git)
* As input file we use a CSV [file](http://dati.toscana.it/dataset/ceb33e9c-7c80-478a-a3be-2f3700a64906/resource/5e8ec560-cbe6-4630-b191-e274218c183c/download/strutturericettive20141012.csv) provided by RET.


1. Start OpenRefine, a new web browser window should open automatically, or you can point it to *http://localhost:3333* (default conf). On the **Create Project** tab select the CSV file to upload it.

![Create project]
(https://github.com/andreybratus/tutorial/blob/master/img/create-project.png)

Click on the next button to upload the file to OpenRefine. On the next screen additional project configurations can be set.

![Create project]
(https://github.com/andreybratus/tutorial/blob/master/img/create-project2.png)

OpenRefine attempts to identify the file format, separator type automatically, so we can click "Create Project" button.

On the project screen we have a preview of our tabular data and we identify following problems that we want to clean:

* In column "nome" all values are in uppercase, which we want are going to edit into titlecase, such that:
> LA VALLE DEI MEDICI => La Valle Dei Medici

* In columns "lt" and "lg" we have numerical values that represent latitude, longitude cordinates which in some cases have to many digits after the decimal point. Therefore we want to limit the amount of digits after the decimal point to 2, such that:
> 37.40425419999999689935066271 will become 37.40

2. To correct all the values in column "nome" click on the arrow near the column title and choose:
> Edit cells --> Common transforms --> To titlecase

![To titlecase transform]
(https://github.com/andreybratus/tutorial/blob/master/img/titlecase.png)
