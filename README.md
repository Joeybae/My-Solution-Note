# My-Solution-Note

여지까지 헤매거나, 어려웠던 문제들의 해결한 방법을 정리하는 노트

-------------------------------

1월 2일

  - 문제점 : exports.login_info = login_info; 가 작동안됨
  
        request(options, function (error, response) {
          if (error) throw new Error(error);
          let login_info = JSON.parse(response.body);
          console.log(login_info);
          exports.login_info = login_info;
        });

  - 해결방법 : 자바스크립트의 비동기 처리방식
  
  자바스크립트의 비동기 처리란 특정 코드의 연산이 끝날 때까지 코드의 실행을 멈추지 않고 다음 코드를 먼저 실행하는 자바스크립트의 특성을 의미하는데, 문제점에서 처럼 exports로 안내보내지고, request 안에서 필요한 작업을 수행해야한다.
  
        request(options, function (error, response) { 
          if (error) throw new Error(error);
          let login_info = JSON.parse(response.body);
          //console.log(login_info);
          let message = login_info.message;

          if (message === 'ok'){
            res.send(login_info);
          } else {
            res.send('아이디 또는 비밀번호가 틀렸습니다.')
          }
        });
