# tableToExcel
port to excel,has several steps to do.
# first,you need to install two dependencies(sometimes,you need to install three dependencies according to tips)
    npm install -S file-saver xlsx
    npm install -D script-loader
# second,Create a new js file,to place Blob.js and Export2Excel.js
# last,write these two methods
        exportExcel(tabHeaderName,tableData,excelName){
                let that = this,
                    title = [],
                    titleParam = [];   
                for(let i = 0;i < tabHeaderName.length;i++){
                    title.push(tabHeaderName[i].title);
                    titleParam.push(tabHeaderName[i].key);
                }
          require.ensure([], () => {
                    const tHeader = title,
                        filterVal = titleParam,
                        list = tableData,
                        data = that.fJson(filterVal, list),
                        fileName = excelName;
                        var strFileName = fileName.replace(/(.*\/)*([^.]+).*/ig,"$2");
                        strFileName = fileName;
                portExcel(tHeader, data, strFileName);
          })
        },
        fJson(filterVal, jsonData) {
          return jsonData.map(v => filterVal.map(j => v[j]))
        }
# note:tabHeaderName refers to the name of the header;tableData refers to the data obtained from the backend;excelName refers to the name of the excel table.of course,when the table data is enough, you need to pagination,you need to obtained interface from the backend(This method can only export the current page data)
