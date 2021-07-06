<div class="axi-header">
  <h1>Tabular Operators</h1>
</div>

## where operator 

Sorts out a dataset to a branch of rows that meets a *state* when executed.

```
['http-logs']
| where method == 'GET'
```

| **Syntax** | **Arguements**  | **Returns** |
|----------------|------------------------------------|---------------| 
|  ['http-logs'] `where` *state*    |  **`http-logs`:** The dataset whose events are to be filtered, **state**: a bool expression over the columns of the dataset `http-logs` , it's then checked for each row in `http-logs` | Row in dataset `http-logs` for which *state* is true.  |

### Example

```
['http-logs']
| where method == 'GET' and content_type == 'image/jpeg'
```

## scan operator 

Scans figures, data, equivalent, and then creates results established on the operator setup. The output of the corresponding data is specified by the input data defined in the operators step. 

## count operator 

Returns the number of events and all matching events from the dataset. 

| **Syntax** | **Arguements**  | **Returns** |
|----------------|------------------------------------|---------------| 
|  ['http-logs']  count   |  **['http-logs']:** dataset whose events are to be counted | a table with a single data and column with. The value of the only cell is the number of events in `http-logs`.

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