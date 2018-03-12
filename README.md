# Switch
A simple circuit breaker library to provide reliability

Example:
```
const cb = create(()=>{
  if(Math.random() < 0.5) {
    return Promise.reject("primary err");
  }else {
    return Promise.resolve("primary");
  }
},()=>{
  if(Math.random() < 0.2) {
    return Promise.reject("secondary err");
  }else {
    return Promise.resolve("secondary");
  }
},()=>{
  return true;
},(stats)=>{
  console.log(stats);
  return stats.callsToSecondary > 2;
});

cb([true])
.then((r)=>{
 console.log(r);
});
```


