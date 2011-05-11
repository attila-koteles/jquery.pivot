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
        
        // Fires after we added a the grouping colums
        // pivot_values => [ { 'col_data': Object, 'tree_node': Object, 'pivot_sum': 845}, { ... }, ... ]
        // You can use it to override the default behaviour and add new colums, change order, hide items
        // Calculate different "totals" (average?)
        onRowAppendPivotValues: function (pivot_values, row_to_append) {
            appendPivotValues(pivot_values, row_to_append);
        },

        // Similar as above you can override the pivot table header drawing functions
        onRowAppendPivotHeaders: function(pivotCols, row) {
            appendPivotHeaders(pivotCols, row);
        },

        onResultCellClicked: null, //Method thats called when a result cell is clicked. This can be used to call server and present details for that cell.
        noGroupByText: "No value", //Text used if no data is available for specific groupby and pivot value.
        noDataText: "No data" //Text used if source data is empty.
    };