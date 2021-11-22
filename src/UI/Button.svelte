<script>
    export let mode = null;

</script>
<!-- HTML !-->
<button class="{mode}" on:click><slot/></button>


<style>
  button{
    z-index: 1;
  }
.confirm {
  align-items: center;
  background-color: initial;
  background-image: linear-gradient(rgba(179, 132, 201, .84), rgba(57, 31, 91, .84) 50%);
  border-radius: 42px;
  border-width: 0;
  box-shadow: rgba(57, 31, 91, 0.24) 0 2px 2px,rgba(179, 132, 201, 0.4) 0 8px 12px;
  color: #FFFFFF;
  cursor: pointer;
  display: flex;
  font-family: Quicksand,sans-serif;
  font-size: 18px;
  font-weight: 700;
  justify-content: center;
  letter-spacing: .04em;
  line-height: 1rem;
  margin: 0;
  padding: 18px 18px;
  text-align: center;
  text-decoration: none;
  text-shadow: rgba(255, 255, 255, 0.4) 0 0 4px,rgba(255, 255, 255, 0.2) 0 0 12px,rgba(57, 31, 91, 0.6) 1px 1px 4px,rgba(57, 31, 91, 0.32) 4px 4px 16px;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: baseline;
}

.confirm:hover {
  background-image: linear-gradient(#B384C9, #391F5B 50%);
}

@media (min-width: 768px) {
  .confirm {
    font-size: 21px;
    padding: 18px 34px;
  }
}

/* CSS */
.delete {
  font-size: 16px;
  font-weight: 200;
  letter-spacing: 1px;
  padding: 13px 20px 13px;
  outline: 0;
  border: 1px solid black;
  cursor: pointer;
  position: relative;
  background-color: rgba(0, 0, 0, 0);
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.delete:after {
  content: "";
  background-color: #f1dba9;
  width: 100%;
  z-index: -1;
  position: absolute;
  height: 100%;
  top: 7px;
  left: 7px;
  transition: 0.2s;
}

.delete:hover:after {
  top: 0px;
  left: 0px;
}

@media (min-width: 768px) {
  .delete {
    padding: 13px 50px 13px;
  }
}
</style>