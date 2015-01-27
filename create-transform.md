Tutorial to create a simple transform with OpenRefine
=====================================================

Requirements for this tutorial:

* Install **OpenRefine** from [here](http://openrefine.org) or clone and build it from source [git](https://github.com/OpenRefine/OpenRefine.git)
* As input file we use a CSV [file](http://dati.toscana.it/dataset/ceb33e9c-7c80-478a-a3be-2f3700a64906/resource/5e8ec560-cbe6-4630-b191-e274218c183c/download/strutturericettive20141012.csv) provided by RET.

Tutorial
---------
1. Start OpenRefine, a new web browser window should open automatically, or you can point it to *http://localhost:3333* (default configuration). On the **Create Project** upload the aforementioned CSV file.

![Create project]
(https://github.com/andreybratus/tutorial/blob/master/img/create-project.png)

OpenRefine attempts to identify file format automatically and allows to configure data importing.

![Create project]
(https://github.com/andreybratus/tutorial/blob/master/img/create-project2.png)

Our input file format is recognized well, so go ahead and click on *Create Project*.

On the project screen we have a preview of our tabular data entries such that we can easily identify the following problems that we want to clean:

* In column "nome" all values are in uppercase, which we want to transform into CammelCase, such that:
> LA VALLE DEI MEDICI ---> La Valle Dei Medici

* In columns "lt" and "lg" we have numerical values that represent latitude, longitude cordinates. Some entries appear have to many digits after the decimal point. Therefore, we want to limit the amount of digits after the decimal points to 2 digits, such that:
> 37.40425419999999689935066271 ---> 37.40

2. To correct all the values in column "nome" click on the arrow near the column title and choose:
> *Edit cells --> Common transforms --> To titlecase*

![To titlecase transform]
(https://github.com/andreybratus/tutorial/blob/master/img/titlecase.png)
