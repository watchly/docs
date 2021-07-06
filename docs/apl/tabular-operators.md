<div class="axi-header">
  <h1>Tabular Operators</h1>
</div>


**All examples are calculated in the `http-logs` dataset**
## where operator 

Sorts out a dataset to a branch of rows that meets a *state* when executed.

### Syntax

 ['<dataset name>'] `where` *state* 

| **Arguements**  | **Returns** |
|------------------------------------|---------------| 
| **`http-logs`:** The dataset whose events are to be sorted,                                                          
<br> **state**: a bool expression over the columns of the dataset `http-logs` , it's then checked for each row in `http-logs` | Row in dataset `http-logs` for which *state* is true.  |
### Example

```
['http-logs']
| where method == 'GET' and content_type == 'image/jpeg'
```
## scan operator 

Scans figures, data, equivalent, and then creates results established on the operator setup. The output of the corresponding data is specified by the input data defined in the operators step. 
## count operator 

Returns the number of events and all matching events from the dataset. 

### Syntax

['<dataset name>'] | count


| **Arguements**  | **Returns** |
|------------------------------------|---------------| 
| **['http-logs']:** dataset whose events are to be counted |  a table with a single data and column with. The value of the only cell is the number of events in `http-logs`.

### Example 

```
['http-logs']
| where method == 'GET'
| count 

```

```
['http-logs']
| count 
```
## extend operator 

Create calculated columns and attach them to the result set.

### Syntax

`<dataset name>` `|extend` [ColumnName|(ColumnName[, ...])=]Expression [, ...] 

| **Arguements**  | **Returns** |
|---------------------------------------|----------------------------------| 
| **['http-logs']:** The input dataset table. <br> **ColumnName:** The name of the column to add or update. *ColumnName* can be the field of your dataset, they are automatically generated for you and a list of column names can be specified in parentheses, Expression: A calculation over the columns of the input. <br> **Expression:** A calculation over the columns of the input.| Column names noted by extend that already exist in the input are removed and appended as their new calculated values.<br> Column names noted by extend that do not exist in the input are appended as their new calculated values.|

### Example

```
['http-logs']
| where _time >= ago(2d)
| extend method , ['geo.city'], ['geo.country'], content_type

```

