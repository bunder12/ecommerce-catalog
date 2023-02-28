<script>
    export default{
        props: {

        },
        methods: {
            handleNext(){
                this.$emit('sendCount', this.count += 1)
            }
        }
    }
</script>

<template>
        <div class="rectangle-found"></div>
        <div class="card-found">
            <div class="areaimg-found">
                <img class="img-found" src="../assets/sad-face.svg"/>
            </div>
            <div class="areacontent-found">
                <p>This product is unavailable to show {{ count }}</p>
                <button @click="handleNext" class="btnNext-found">Next Product</button>
            </div>
        </div>
</template>

<style scoped>
    .rectangle-found {
    position: absolute;
    background-color: var(--background-found);
    width: 100%;
    height: 70%;
    z-index: 10;
    left: 0;
    top: 0;
    }

    .card-found {
    position: relative;
    border-radius: 10px;
    z-index: 20;
    width: 80%;
    height: 65%;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    background-color: var(--background-default);
    padding: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    }

    .areaimg-found{
    width: 80%;
    height: 80%;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
  }

  .img-found{
    width: 100%;
    height: 100%;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
  }

    .areacontent-found{
    width: 50%;
    text-align: center;
    z-index: 80;
    }

    .btnNext-found{
    z-index: 40;
    border:2px solid var(--background-black);
    outline: none;
    background-color: transparent;
    color: var(--background-black);
    width: 48%;
    padding: 10px 0px;
    cursor: pointer;
    margin-top: 20px;
    }

    @media (max-width: 767px) {
        .areacontent-found{
            width: 100%;
        }

        .btnNext-found{
            width: 60%;
        }
    }
</style>