<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p>{{JSON.stringify(products)}}</p>
  </div>
</template>

<script>
 export default{
   data(){
     return{
       str:"yidaunwenzi",
       products:[]
     }
   },
   mounted(){
    //  window.clipboardData.setData(this.str);
    this.axios.get("/all_pro").then(res=>{
      var product1=res.data;
      console.log(res.data);
      product1.forEach((elem)=>{
        var obj={};
        obj.image=elem.Pimage.split(",")[0];
        obj.name=elem.Pname;
        obj.desc=elem.Pdesc,
        obj.pid=elem.Pid;
        obj.liked=parseInt(Math.random()*30);
        obj.descimages=elem.Pimage.split(",");
        obj.sold=elem.Psold;
        obj.total=elem.Ptotal;
        obj.discount=1;
        obj.factory=elem.Pmanu;
        obj.keywords=elem.Pkeyword;
        obj.type=elem.Ptype;
        obj.spec=elem.Spec;
        obj.price=elem.Sprice;
        this.products.push(obj);
      })
      console.log(this.products)
    })
    var products = {
    image: '123.jpg',
    name: '初音未来',
    desc: "物美价廉，人见人爱",
    pid: '2815647',
    liked: 0,
    specs: [
        {
            spec: "现货",
            price: 1296
        },
        {
            spec: "预定",
            price: 200
        }
    ],
    descimages:["2815647_1.jpg"],
    sold: 15,
    total: 50,
    discount: 1,
    factory: "良笑舍",
    keywords: "初音未来"
}
   }
}
</script>

<style>
.about{
  cursor: text;
  user-select:text;
}
</style>
