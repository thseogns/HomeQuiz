<script>
    import {languages ,tableNumber} from "../mock"
    //img Start
    import dropdown from "../public/images/chevron-down.png"
    import notifications from "../public/images/notifications_active.png"
    import bill from "../public/images/receipt.png"
    import cart from "../public/images/shopping_cart.png"
    import table from "../public/images/table.png"
    //img End
    let isDropdownOpen = false
    let language = languages[0].name
    
    const toggleHandler =()=>{
        console.log(languages)
        isDropdownOpen = !isDropdownOpen;

    }
    const languageChangeHandler=(e)=>{
        console.log(e.target.innerText)
        language=e.target.innerText
        isDropdownOpen = !isDropdownOpen;
    }
    const notificationHandler = ()=>{
        alert("Waiter Called")
    }
</script>
<nav>
    <ul>
        <li>
            
          <button class="toggle_flex button" on:click={ toggleHandler }>
            <div>{language}</div>  
            <div >
                <img src={dropdown} alt="dropDown"/>
            </div >
          </button>
        </li>
        {#if isDropdownOpen}
        <ul class="dropdown-menu">
            <li class="languages">
                <button class="button" on:click={languageChangeHandler}>
                    {languages[0].name}
                </button>
            </li>
            <li class="languages button">
                <button class="button" on:click={languageChangeHandler}>
                    {languages[1].name}
                </button>
            </li>
        </ul>
        {/if}
        <li>
          
           <button class="waiter_flex button" on:click={notificationHandler}>
            <div>
            <img src={notifications} alt="notifications"/>
            </div>
            <div>Call Waiter</div>
            </button>
        </li>
        <li>
           <div><img src={bill} alt="bill"/></div>
           <div class="selected_n">View Bill</div>
        </li>
        <li>
           <div><img src={cart} alt="cart"/></div>
           <div class="selected_n">My Cart</div>
           <div><div class="cart_number">0</div></div>
        </li>
        <li>
           <div><img src={table} alt="table"/></div>
           <div class="table_number">{tableNumber}</div>
        </li>
    </ul>
</nav>

<style>
    nav{
         background-color: #24201F;
         height: 80px;
         
    }
    nav ul {
        padding: 0;
        display: grid;
        grid-template-columns: 0.6fr 1fr 1fr 1fr 0.4fr;  
        margin: 0;
    }
    .toggle_flex ,  .waiter_flex, .dropdown-menu .languages button{
        display: flex;
        line-height:3;
        width: 100%;
        justify-content: space-between;
    }
 
    .toggle_flex div ,  .waiter_flex div{
        height: 100%;
    }
    .dropdown-menu{   
        background-color: rgb(168, 134, 134);
        left: 0;
        position: absolute;
        display: flex;
        flex-direction: column;
        margin-left:20px;
        text-align: start;
        
        top: 80px;
        width: 13%;
        z-index: 99;
       
     
    }
   
    nav ul li,.waiter_flex{
        height: 80px;
        display: flex;
        justify-content: center;
        list-style: none;
        border-right:1px solid white;
        gap: 12px;
        font-size: 30px;
        
      
    }
    nav ul li:nth-child(2){
        padding: 0;
    }
  
    .selected_n{
        color:  #AEABA6;

    }
    nav ul li:first-child{
        position: relative;
        justify-content: space-between;
        padding: 0 25px;
       
    }
    nav ul li:last-child{
      border: none;
      font-size: 40px;
    }

    nav ul li div{
        font-weight: bold;
       color: white;
       display: flex;
       align-items: center;
       justify-content: center;
    }
    img{
    
        width: 40px;
        height: 40px;

        
    }
    .dropdown-menu .languages{
      
        padding: 0 8px;
        margin: 0;

    }
    .dropdown-menu .languages:last-child{
        border-top: 1px solid white;
    }

    
    .button{
        border: none;
        font-size: 30px;
        background-color: transparent;
        cursor: pointer;
        color: white;
    }
 
    .table_number{
        font-weight:bold ;
    }
    .cart_number{
        width: 50px;
        height: 50px;
        background-color: #55524D;
        border-radius: 50%;
        font-weight: bold;
        color:  #AEABA6;
    }
</style>