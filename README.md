# My-Solution-Note

여지까지 헤매거나, 어려웠던 문제들의 해결한 방법을 정리하는 노트

-------------------------------

1월 2일

  - 문제점 : 자바스크립트의 비동기 처리방식으로 exports.login_info = login_info; 가 작동안됨
  
        request(options, function (error, response) {
          if (error) throw new Error(error);
          let login_info = JSON.parse(response.body);
          console.log(login_info);
          exports.login_info = login_info;
        });

  - 해결방법 : 콜백함수
  
         function getData(callbackFunc){
          request(options, function (error, response) {
            if (error) throw new Error(error);
            let login_info = JSON.parse(response.body);
            callbackFunc(login_info);
          });
         }

         //callback
        getData(function(tableData){
          console.log(tableData);
        });
