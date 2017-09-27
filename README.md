# GiGA Genie 2048
GiGA Genie 서비스SDK를 이용한 2048 게임입니다. 

### 사용한 API
Best Score를 appdata API로 구현했습니다.

 1. `appdata.createNameSpace`로 Best Scroe를 저장할 namespace 생성

        function createnamespace(){
         var options={};
         options.namespace="bestscore";
         options.shareflag='N';
         gigagenie.appdata.createNameSpace(options,function(result_cd,result_msg,extra){
                if(result_cd===200){
                        console.log("Namespace creation is success.");
                } else{
                        console.log("Namespace creation is fail.");                        
                }
          });
        }

 2. `appdata.setKeyData`로 Best Score 저장
 
        function setkeydata(score){
          var options={};
          options.namespace='bestscore';
          options.key='bestscore';
          options.data=score;
          gigagenie.appdata.setKeyData(options,function(result_cd,result_msg,extra){
                if(result_cd===200){
                        console.log(options.key);
                } else {
                        console.log("Error");
                }
          });
        }
 3. `appdata.getKeyData`로 Best Score 가져오기
 
        function getkeydata(){
          var options={};
          options.namespace='bestscore';
          options.key='bestscore';
          gigagenie.appdata.getKeyData(options,function(result_cd,result_msg,extra){
                if(result_cd===200){
                        console.log('getKeyData:'+extra.data);
                        document.getElementById('bestscore').innerHTML=extra.data;
                } else document.getElementById('bestscore').innerHTML="0";
          });
        }



## License
2048 is licensed under the [MIT license.](https://github.com/gabrielecirulli/2048/blob/master/LICENSE.txt)
