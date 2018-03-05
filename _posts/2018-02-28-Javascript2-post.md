---
layout: post
title: "자바스크립트로 HTML 테이블을 엑셀로 Export 하기 (IE9 이하 오류 해결)"
excerpt: HTML table export as excel in js
categories: [hello world]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---


### fnExcelReport 함수를 이용한 엑셀 export작업은 ie10부터 지원하므로 이 문제를 해결하고자 함
#### 기존 fnExcelReport 함수에 try-catch 코드를 추가하였음. 

1.

    ```javascript
      <script type="text/javascript">
        function fnExcelReport(id, name) {
              var tab_text = '<html xmlns:x="urn:schemas-microsoft-com:office:excel">';
              tab_text = tab_text + '<head><xml><x:ExcelWorkbook><x:ExcelWorksheets><x:ExcelWorksheet>';
              tab_text = tab_text + '<x:Name>Sheet1</x:Name>';
              tab_text = tab_text + '<x:WorksheetOptions><x:Panes></x:Panes></x:WorksheetOptions></x:ExcelWorksheet>';
              tab_text = tab_text + '</x:ExcelWorksheets></x:ExcelWorkbook></xml></head><body>';
              tab_text = tab_text + "<table border='1px'>";
              var exportTable = $('#' + id).clone();
              exportTable.find('input').each(function (index, elem) { $(elem).remove(); });
              tab_text = tab_text + exportTable.html();
              tab_text = tab_text + '</table></body></html>';
              var fileName = name + '.xls';
    
              // ie 10+
              try{
                  var blob = new Blob([tab_text], { type: "application/vnd.ms-excel;charset=euc-kr" })
                  window.saveAs(blob, fileName);
              }
              // ie 9이하
              catch(e){
                  var data = document.getElementById(id);
                  var csvData = [];
                  var tmpArr = [];
                  var tmpStr = '';
                  for (var i = 0; i < data.rows[0].cells.length; i++)
                  {
                  tmpArr.push((data.rows[0].cells[i].innerText || data.rows[0].cells[i].textContent));
                  }
                  csvData.push(tmpArr.join('\t'));
                  for (var i = 1; i < data.rows.length; i++)
                  {
                  tmpArr = [];
                  for (var j = 0; j < data.rows[0].cells.length; j++)
                  {
                      tmpArr.push(data.rows[i].cells[j].innerHTML);
                  }
                  csvData.push(tmpArr.join('\t'));
                  }
                  var output = csvData.join('\n');
                  SaveContents(output);
              }    
          }
        </script>
        
    ```

새로 추가된 코드가 실행되면(ie9일 때) 파일 저장 팝업이 뜨고, 파일명 수정할 수 있음.
파일 저장 형식이 html파일로 나타나지만 실제로 저장해 보면 xls 파일로 잘 저장됨.