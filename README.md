# UFOs

**Overview and Purpose**

Dana’s webpage and dynamic table are working as intended, but she’d like to provide a more in-depth analysis of UFO sightings by allowing users to filter for multiple criteria at the same time. In addition to the date, you’ll add table filters for the city, state, country, and shape.

This new assignment consists of one technical analysis deliverable and a written report. You will submit the following deliverables:

  * Deliverable 1: Filter UFO sightings on multiple criteria
  * Deliverable 2: A written report on the UFO analysis (README.md)

**Results**
 * Describe to Dana how someone might use the new webpage by walking her through the process of using the search criteria. Use images of your webpage during the filtering process to support your explanation.

_code:_
// from data.js
const tableData = data;

// reference the HTML table(output) using d3 library
var tbody = d3.select('tbody');

// Function of populate data into html table
function buildTable(data) {
    // init table data
    tbody.html('');

    // first array loop for <tr>
    data.forEach((dataRow) => {
        let row = tbody.append('tr'); //html
        //second loop for <td>
        Object.values(dataRow).forEach((val) =>{
            let cell = row.append('td'); //html
            // d3 funtion 
            cell.text(val);
        });
    });

};

// EXTRA: Create a variable to keep track of all the filters as an object.
var clearEntries = d3.select("#clear-btn");
clearEntries.on("click", function() {
  location.reload();
});



// 1. Create a variable to keep track of all the filters as an object.
var filters = {
};

// 3. Use this function to update the filters. 
function updateFilters() {

    // 4a. Save the element that was changed as a variable.
    let inputElement = d3.select(this);

    // 4b. Save the value that was changed as a variable.
    let inputValue = inputElement.property("value");

    // 4c. Save the id of the filter that was changed as a variable.
    let inputID = inputElement.attr("id");
  
    // 5. If a filter value was entered then add that filterId and value
    // to the filters list. Otherwise, clear that filter from the filters object.

      if (inputValue) {
        filters[inputID] = inputValue;
    } else{filters ={};};
  
  
    // 6. Call function to apply all filters and rebuild the table
    filterTable(filters);
};

// 7. Use this function to filter the table when data is entered.
function filterTable(obj) {
  
    // 8. Set the filtered data to the tableData.
    let filteredData = tableData;
  
    // 9. Loop through all of the filters and keep any data that
    // matches the filter values
    Object.entries(obj).forEach(([fkey, fval]) =>{
        
      filteredData = filteredData.filter((row) => row[fkey] === fval)
          

  });
  
    // 10. Finally, rebuild the table using the filtered data
    buildTable(filteredData);
};
  
  // 2. Attach an event to listen for changes to each filter
  d3.selectAll("input").on("change",updateFilters);
  
  // Build the table when the page loads
  buildTable(tableData);
  
<img width="939" alt="image" src="https://user-images.githubusercontent.com/99268646/166502427-d83ec203-3dc1-4be7-b814-cc0db802ba7b.png">

<img width="939" alt="image" src="https://user-images.githubusercontent.com/99268646/166502744-c5998ef7-9ca3-40c3-8def-ab11565c137f.png">

_Steps_: 

 * Use the line file:///C:/Users/lette/Desktop/Module%2011/Challenge/index.html
 * Use the filter search (image above) 
 * With the filter search, can enter in Date, City, State, Country and Shape 
 * Click "Filter Table" OR "Clear Table" 


**Summary**



