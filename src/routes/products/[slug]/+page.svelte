<script>
import {page} from "$app/stores"
import {categories, products} from "../../../mock"
const productName = $page.params.slug
let matchedCategory = null;
let matchedProducts = [];
let description = ""
for (const key in categories) {
    if (categories[key].name === productName) {
      const matchedCategory = categories[key];

      const productOrder = matchedCategory.productOrder;
      description = matchedCategory.description;

      
      for (const productId of productOrder) {
        const matchingProduct = products[productId];
        if (matchingProduct) {
          matchedProducts.push(matchingProduct);
        }
      }
    }
  }
console.log(matchedCategory)
</script>
<div class="main_cover">
    {#if matchedProducts.length > 0}
        <div class="arrow flex">
            <a href="/" ><div class="link">←</div></a>
            <div class="flex">
                <h1>{productName}<span> &nbsp&nbsp&nbsp&nbsp  · &nbsp&nbsp&nbsp&nbsp { description}</span></h1> 
                     
            </div>
        </div>
    <ul class="list_cover">
        {#each matchedProducts as product}
    
        {#if product.picture===undefined}
        <li class="list none_picture_list">
            <div class="none_picture">
            {product.name}
            </div>
            <p>{product.name}</p>
            
            <p>${(product.price / 100).toFixed(2)} </p>
        
        </li>
        {:else}
        <li class="list">
            <div class="menu_cover">
            <img src={product.picture} alt={product.id}/>
            </div>
            <p>{product.name}</p>
            
            <p>${(product.price / 100).toFixed(2)} </p>
        
        </li>
        {/if}
        
        {/each}
    </ul>
    {/if}
</div>

<style>
.main_cover{
    margin: 30px;
}
.arrow{
gap: 45px;
margin-bottom:30px ;
}
.flex{
    display: flex;
}
h1{
    margin: 0;
    font-size: 50px;
}
span{
    font-size: 30px;
    font-weight: 500;
    color:  #5c5a56;
}

.link{

    width:100px;
    height: 70px;
    box-shadow: 0 0 20px rgba(0, 0, 0 , 0.3) ;
  
    text-align: center;
    line-height: 60px;
    color: black;    
    border-radius: 15px;
}
a{
    text-decoration: none;
    font-size: 40px;
    font-weight: bold;
   

  

}
/*LIST*/
.list_cover{
        
     
        display: grid;
        grid-template-columns: 1fr 1fr 1fr ; 
       
      
      
       margin: 0;
       padding: 0;
        gap: 18px;
    }
.list{
    list-style: none;
 
}

.list img{
    border-radius: 15px;
   width: 100%;
   object-fit:cover;
}
p{
    font-size: 25px;
    font-weight:normal;
    text-align: center;
    color: black;
    margin: 10px;
   
}
p:last-child{
    color:  #5c5a56;
    margin-bottom: 18px;
}
.none_picture_list{
display: flex;
flex-direction: column;
justify-content: end;
}
.none_picture{
    background-color: #ececec;
    border-radius: 15px;
   width: 100%;
 height: 100%;
 color: white;
 font-size: 50px;
 font-weight: bold;
 padding: 20px 30px;
}
.none_picture_list p:last-child{
    margin-bottom: 13px;
}

</style>