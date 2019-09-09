const express = require('express')
const app = express()
const port = 8000;
const fetch = require("node-fetch");
const fs = require('fs');
//var json2xls = require('json2xls');


const csvjson = require('csvjson');

var current_time=new Date().getTime();
//console.log(current_time);
 
    //customData.league.id=data.league;


   app.get("/",function(req,res){
     console.log("new request get");
     console.log("Calling API.....");
     fetch('https://api.stratz.com/api/v1/match/4137423068')
     .then(response => response.json())
     .then(data => {
        // var mydata=JSON.parse(data);
       console.log("Converting in to csv and data length is- ",Object.keys(data).length);
      
       var customData=[];
      //  customData.id=data.id;
      //  customData.leagueDetails=data.league;
       customData.push= JSON.stringify(data);

console.log(data['id']);

    res.send("customData");
   })
  
   
  });
   
   
   
   
    //convert csv and wrive in csv file

  //   const csvData = csvjson.toCSV(data, {
  //     headers: 'key'
  // });
  //   fs.writeFile(current_time+'.csv', csvData, function (err) {
  //      if (err) throw err;
  //      console.log('saved file');
  //  });
    

  //with promises
  var promise1 = new Promise(function(resolve, reject) {
    fetch('https://api.stratz.com/api/v1/match/4137423068')
       .then(response => response.json())
       .then(data => {
          // var mydata=JSON.parse(data);
         console.log("Converting in to csv and data length is- ",Object.keys(data).length);
        
       resolve(data);
  
  
     })
  });
  
  promise1.then(function(value) {
    console.log(value);
    // expected output: "foo"
  });
  
  console.log(promise1);
  // expected output: [object Promise]

   
 






app.listen(port, () => console.log(`Example app listening on port ${port}!`));
