Tutorial to create a simple transform with OpenRefine
=====================================================

This tutorial describes the process of perfmorning data cleaning operations with OpenRefine and how to extract transformation rules that we use to clean a specific dataset. These rules can be later used to pass to the Batchrefine [transformer](https://github.com/fusepoolP3/p3-batchrefine).

Requirements for this tutorial:

* Install **OpenRefine** from [here][openrefine] or clone and build it from source [git](https://github.com/OpenRefine/OpenRefine.git)
* As input file we use a CSV [file](http://dati.toscana.it/dataset/ceb33e9c-7c80-478a-a3be-2f3700a64906/resource/5e8ec560-cbe6-4630-b191-e274218c183c/download/strutturericettive20141012.csv) provided by RET.

Tutorial
---------
1. Start OpenRefine, a new web browser window should open automatically, or you can point it to *http://localhost:3333* (default configuration). On the **Create Project** tab upload the aforementioned CSV file.

<div align="center">
<img src="/img/create-project.png" alt="Create project" width="60%" height=60%>
</div>


OpenRefine attempts to identify input file format automatically but allows to configure data importing (format, separator type, etc.)


<div align="center">
<img src="/img/create-project2.png" alt="Create project" width="75%" height=75%>
</div>

Our input file format should be recognized correctly, so go ahead and click on *Create Project*.


### Identify problems with data
On the project screen we have a preview of our tabular data entries and we can easily identify the following problems that we want to clean:

* In column "nome" all entries are in uppercase, which we want to transform into CammelCase, such that:
> LA VALLE DEI MEDICI ---> La Valle Dei Medici

* In columns "lt" and "lg" we have numerical values that represent latitude, longitude coordinates. Some entries appear have to many digits after the decimal point. Therefore, we want to limit the amount of digits after the decimal points to 2 digits, such that:
> 37.40425419999999689935066271 ---> 37.40

### Perform cleaning


1. To transform all the entries in column "nome" into CamelCase click on the arrow near the column title and select:
> Edit cells --> Common transforms --> To titlecase*

<div align="center">
<img src="/img/titlecase.png" alt="To CamelCase transform" width="70%" height=70%>
</div>

2. Fixing the lenght of coordinates in columns "lt" and "lg" is performed in two steps:
* Parse the string values to have them identified as numbers by clicking on the arrow near the column title and selecting:
> Edit cells --> Common transforms --> To number

<div align="center">
<img src="/img/to-number.png" alt="Parse number" width="60%" height=60%>
</div>

Numeric entries are represented with green color. Perform the same task for both columns.

* In the next step we will round the numeric values to 2 digits after the decimal point. Open the transform window by clicking on the arrow near the column title and selecting:
> Edit cells --> Transform
In this window we can apply custom transformations on column entries by writing expressions in one of the available languages (Google Refine Expression Language [(GREL)}(https://github.com/OpenRefine/OpenRefine/wiki/Google-refine-expression-language), Clojure or Jython.
In this tutorial we use Jython as an example:
```
return round(value,2)
```

<div align="center">
<img src="/img/round.png" alt="Jython expression" width="60%" height=60%>
</div>


You can preview the result of an expression before applying it on the whole dataset. To complete the transform click OK.

### Extract transformation rules
OpenRefine keeps track of all changes you apply to a dataset and allows you to undo or redo them using the history entries that are listed in **Undo/Redo** tab. Moreover, you it allows you to extract transformation rules in as a JSON array. Each element of an array is a JSON object describing a transformation rule.

<div align="center">
<img src="/img/extr-transform.png" alt="Extract transform rules" width="67%" height=67%>
</div>



To save transformation rules for later use click on the extract button of the history panel and copy its contents to a file. Use such transformation rules file to pass to the Batchrefine transformer together with the corresponding dataset. 


[openrefine]: http://openrefine.org "OpenRefine"
