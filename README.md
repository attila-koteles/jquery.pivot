The jquery.pivot plugin can be used for presenting table data in pivot form. It is made and maintained Janus Schmidt.
The project lives on github. You can find it at http://github.com/janusschmidt/jquery.pivot.

###Defaults

    $.fn.pivot.defaults = {
        source: null, //Must be json or a jquery element containing a table
        
        bSum: true, //If you are pivoting over non numeric data set to false.
        rowTotals: true, // Should we calculate row total?
        colTotals: true, // Should we calculate column total?
        bCollapsible: true, // Set to false to expand all and remove open/close buttons

        rowTotalCaption: 'Total',
        colTotalCaption: 'Total',

        formatFunc: function (n) { return n; }, //A function to format numeric result/total cells. Ie. for non US numeric formats
        parseNumFunc: function (n) { return +n; }, //Can be used if parsing a html table and want a non standard method of parsing data. Ie. for non US numeric formats.
        
        // Fires after we added a new row (collapse, draw)
        // pivot_values => [ { 'field': 'your col caption', 'value': 845}, { ... }, ... ]
        // You can use it to add additional table cells, calculations here
        afterRowAddFunc: function (pivot_values, row_to_append) { },

        // You might want to add some extra columns in the header too (if you use the above function)
        extraColumns: [],

        onResultCellClicked: null, //Method thats called when a result cell is clicked. This can be used to call server and present details for that cell.
        noGroupByText: "No value", //Text used if no data is available for specific groupby and pivot value.
        noDataText: "No data" //Text used if source data is empty.
    };