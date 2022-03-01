<template>
      <div className="browser-app">
        <div className="browser-header">
          <img
            src="https://assets.ccbp.in/frontend/react-js/history-website-logo-img.png"
            alt="app logo"
            className="history"
          />
          <div className="search-cont">
            <button className="search-btn" type="button" testid="search">
              <img
                src="https://assets.ccbp.in/frontend/react-js/search-img.png"
                alt="search"
                className="search"
              />
            </button>
            <input
              type="search"
              className="search-input"
              placeholder="Search History"
              v-model="search"
              @change="updateList($event)"
            />
          </div>
        </div>
        <div v-if="newResults.length" >
            <div  :key="browserDetails.id" v-for="browserDetails in newResults">
                <BrowserItem :browserDetails="browserDetails"
                 @deleteItem="$emit('deleteItem',browserDetails.id)"/>
            </div>
        </div>
        <div v-else>
           <div className="history-cont">
               <p className="empty-cont">There is no history to show</p>
           </div>
        </div>
         </div>
</template>


<script>
import BrowserItem from "./BrowserItem.vue";
import { computed, ref } from 'vue';

export default {
    name:'BrowserHistory',
    components:{
        BrowserItem
    },
    props:{
        BrowserHistoryList :Array
    },
    setup(props){
        const search = ref('')

        const newResults = computed(()=>{
          return props.BrowserHistoryList.filter(eachResult =>
       eachResult.title.toLowerCase().includes(search.value.toLowerCase()),
        )
        })

       const updateList= (event)=>{
            search.value = event.target.value
            search.value =''
       }
       const deleteItem = (id)=>{
         props.BrowserHistoryList.filter(eachItem => eachItem.id !== id)
       }
    
 return {search,newResults,updateList,deleteItem}
  }

     
    }
</script>

<style scoped>
.browser-app {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.browser-header {
  background-color: #3367d6;
  display: flex;
  align-items: center;
  justify-content: space-around;
  height: 7vh;
}
@media screen and (max-width: 768px) {
  .browser-header {
    justify-content: space-between;
    padding: 10px;
    height: 8vh;
    width: 100%;
  }
}
.history {
  height: 35px;
  width: 130px;
}
@media screen and (max-width: 768px) {
  .history {
    height: 20px;
    width: 70px;
  }
}
.search-cont {
  display: flex;
  align-items: center;
}
@media screen and (max-width: 768px) {
  .search-cont {
    padding: 5px;
  }
}
.search-btn {
  background-color: #2850a7;
  border: 1px solid #64748b;
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
  height: 40px;
  width: 40px;
  outline: none;
}
@media screen and (max-width: 768px) {
  .search-btn {
    height: 30px;
    width: 30px;
    padding: 5px;
  }
}
.search {
  height: 30px;
  width: 30px;
}
@media screen and (max-width: 768px) {
  .search {
    height: 20px;
    width: 20px;
  }
}
.search-input {
  background-color: #2850a7;
  border: 1px solid #64748b;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
  height: 40px;
  width: 440px;
  color: #ffffff;
  margin-left: 2px;
  outline: none;
  padding: 10px;
}
@media screen and (max-width: 768px) {
  .search-input {
    height: 30px;
    width: 200px;
  }
}
.history-cont {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
@media screen and (max-width: 768px) {
  .history-cont {
    width: 100%;
    
  }
}
.empty-cont {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-size: 30px;
  font-family: 'Sans Serif';
  font-weight: bold;
  color: #64748b;
}
</style>
