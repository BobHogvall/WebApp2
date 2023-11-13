<script setup>
const props = defineProps(['buttonText']);
</script>

<template>
  <div class="cloud-container">
    <div id="background-wrap">
      <div class="cloud">
        <button @click="$emit('cloudClick')" class="cloud-button">{{ props.buttonText }}</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.cloud-container {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

#background-wrap {
  align-self: center;
  bottom: 0;
  margin-top: 10px;
  top: 0;
  z-index: 1000;
  position: relative;
}
.cloud {
  background: #fff;
  background: -moz-linear-gradient(top, #fff 5%, #f1f1f1 100%);
  background: -webkit-gradient(
    linear,
    left top,
    left bottom,
    color-stop(5%, #fff),
    color-stop(100%, #f1f1f1)
  );
  background: -webkit-linear-gradient(top, #fff 5%, #f1f1f1 100%);
  background: -o-linear-gradient(top, #fff 5%, #f1f1f1 100%);
  background: -ms-linear-gradient(top, #fff 5%, #f1f1f1 100%);
  background: linear-gradient(top, #fff 5%, #f1f1f1 100%);
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#fff', endColorstr='#f1f1f1',GradientType=0 );

  -webkit-border-radius: 50px;
  -moz-border-radius: 50px;
  border-radius: 50px;

  -webkit-box-shadow: 0 8px 5px rgba(0, 0, 0, 0.1);
  -moz-box-shadow: 0 8px 5px rgba(0, 0, 0, 0.1);
  box-shadow: 0 8px 5px rgba(0, 0, 0, 0.1);

  height: 30px;
  position: relative;
  width: 87.5px;
}

.cloud:after,
.cloud:before {
  background: #fff;
  content: '';
  position: absolute;
  z-index: -1;
}

.cloud:after {
  -webkit-border-radius: 50px;
  -moz-border-radius: 50px;
  border-radius: 50px;

  height: 25px;
  left: 12.5px;
  top: -12.5px;
  width: 25px;
}

.cloud:before {
  -webkit-border-radius: 50px;
  -moz-border-radius: 50px;
  border-radius: 50px;

  width: 45px;
  height: 45px;
  right: 12.5px;
  top: -22.5px;
}

.cloud-button {
  border: none;
  background-image: linear-gradient(#ffffff, #fefefe, #fbfbfb, #f8f8f8, #f6f6f6);
  text-transform: uppercase;
  font-weight: lighter;
  cursor: pointer;
}

.cloud-button:hover {
  color: #a2a2a2;
}

.cloud-button:active {
  transform: translateY(4px);
}

/* .cloud:hover{
	background: #cdcccc;
	background: -moz-linear-gradient(top,  #cdcccc 5%, #7f7e7e 100%);
	background: -webkit-gradient(linear, left top, left bottom, color-stop(5%,#cdcccc), color-stop(100%,#7f7e7e));
	background: -webkit-linear-gradient(top,  #cdcccc 5%,#7f7e7e 100%);
	background: -o-linear-gradient(top,  #cdcccc 5%,#7f7e7e 100%);
	background: -ms-linear-gradient(top,  #cdcccc 5%,#7f7e7e 100%);
	background: linear-gradient(top,  #cdcccc 5%,#7f7e7e 100%);
	filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#cdcccc', endColorstr='#7f7e7e',GradientType=0 );

	-webkit-border-radius: 50px;
	-moz-border-radius: 50px;
	border-radius: 50px;
	
	-webkit-box-shadow: 0 8px 5px rgba(0, 0, 0, 0.1);
	-moz-box-shadow: 0 8px 5px rgba(0, 0, 0, 0.1);
	box-shadow: 0 8px 5px rgba(0, 0, 0, 0.1);

	height: 30px;
	position: relative;
	width: 87.5px;

	z-index: 10000;

} 

.cloud:before:hover {
	background: #7f7e7e;
} */
</style>
