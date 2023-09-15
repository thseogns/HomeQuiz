<script>
    import {categoryOrder, categories} from "../mock"
    console.log(categories)
    let productRoute=""
    const routeHandler=(name)=>{
        productRoute=name
    }
</script>
<div> 
    <ul class="list_cover">
        {#each Object.keys(categories) as categoryKey}
          {#if categories[categoryKey].productOrder.length > 0}
            <li class="list" key ={ categories[categoryKey].id}>
                <a href={`/products/${productRoute}`} on:click={()=>routeHandler(categories[categoryKey].name)}>
                    <div class="product_cover">
                        <div class="img_cover"><img src={categories[categoryKey].picture} alt={categories[categoryKey].id} /></div> 
                        <div>{categories[categoryKey].name}</div>
                    </div>
                </a>
            </li>
          {/if}
        {/each}
      </ul>
</div>

<style>
    .list_cover{
        padding-top: 24px;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr ; 
      
        gap: 50px; 
       
   
    }
  
    .list{
    list-style: none;
    }
    .product_cover {
        display: flex;
        flex-direction: column;
        align-items: center;
        border-radius: 15px;
        background-color: #FAFAF8;
        padding: 12px 0;
        padding-bottom: 80px;
        
    }
    .product_cover div{
        margin-top: 15px;
        color: black;
        font-weight: bold;
        font-size: 40px;
    }
    .img_cover{
        transform: translateY(-30px);
        width: 250px;
        height: 250px; 
        border-radius: 70%;
        overflow: hidden;

      
    }
    img{
        width: 100%;
        height: 100%;
        object-fit: cover
    }

</style>