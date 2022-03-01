<template>
      <li class="browser-item-cont">
      <div class="browser-details">
        <p class="time">{{ browserDetails.timeAccessed  }}</p>
        <img v-bind:src="browserDetails.logoUrl" alt="domain logo" class="logo" />
        <div>
        <p class="title">{{ browserDetails.title }}</p>
        <p class="domainUrl">{{ browserDetails.domainUrl }}</p>
        </div>
      </div>
      <div class="delete-btn">
        <button
          type="button"
          testid="delete"
          class="button"
          @click="$emit('deleteItem',browserDetails.id)"
        >
          <img
            src="https://assets.ccbp.in/frontend/react-js/delete-img.png"
            alt="delete"
            class="delete"
          />
        </button>
      </div>
    </li>
</template>

<script>
export default {
   name:'BrowserItem',
   props:{
       browserDetails:Object,
   },
 
}
</script>

<style scoped>
.browser-item-cont {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  list-style-type: none;
}
@media screen and (max-width: 768px) {
  .browser-item-cont {
    display: flex;
    align-items: flex-start;
    padding: 0px;
    width: 100%;
  }
}
.browser-details {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.time {
  font-size: 20px;
  font-weight: bold;
  font-family: 'Roboto';
  color: grey;
  margin-right: 10px;
}
@media screen and (max-width: 768px) {
  .time {
    font-size: 10px;
    margin: 5px;
  }
}
.logo {
  height: 25px;
  width: 25px;
  margin-left: 100px;
  margin-right: 15px;
}
@media screen and (max-width: 768px) {
  .logo {
    margin: 5px;
    text-align: start;
  }
}
.title {
  font-size: 18px;
  font-weight: bold;
  font-family: 'Roboto';
  color: grey;
  margin-left: 25px;
  margin-right: 15px;
  margin-right: 5px;
}
@media screen and (max-width: 768px) {
  .title {
    font-size: 12px;
    margin: 5px;
    text-align: start;
  }
}
.domainUrl {
  font-size: 15px;
  font-family: 'Roboto';
  margin-left: 25px;
  margin-right: 15px;
  color: grey;
}
@media screen and (max-width: 768px) {
  .domainUrl {
    font-size: 10px;
    text-align: start;
  }
}
.button {
  background-color: transparent;
  border: none;
  outline: none;
}
@media screen and (max-width: 768px) {
  .button {
    font-size: 10px;
    margin: 5px;
    text-align: start;
  }
}
.delete {
  height: 20px;
  width: 20px;
  margin-right: 5px;
}
@media screen and (max-width: 768px) {
  .delete {
    height: 15px;
    width: 15px;
    text-align: start;
  }
}
.delete-btn {
  display: flex;
  align-items: flex-end;
  margin-right: 20px;
}
</style>