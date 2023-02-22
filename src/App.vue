<template>
    <div v-move class="container">
            <div class="header"></div>
            <div class="content">内容</div>
    </div>
</template>
 
<script setup lang='ts'>
import { directive } from '@babel/types';
import type { Directive, DirectiveBinding } from 'vue';
import { ref, reactive } from 'vue';
// const vMove:Directive<any,void> = (el:HTMLElement,bingding:DirectiveBinding) => {
//     console.log(el,el.firstChild);
//     let moveElement:HTMLElement = el.firstChild as HTMLElement 
//     const mouseDown = (e:MouseEvent) =>{
//         let X = e.clientX - el.offsetLeft
//         let Y = e.clientY - el.offsetTop
//         const move = (e:MouseEvent) => {
//             el.style.left = e.clientX - X + 'px'
//             el.style.top = e.clientY - Y + 'px'
//         }
//         document.addEventListener("mousemove",move)
//         document.addEventListener("mouseup",() => {
//             document.removeEventListener("mousemove",move)
//         })
        
//     }
//     moveElement.addEventListener("mousedown",mouseDown)
// }
const vMove:Directive<any,void> = (el:HTMLElement,bingding:DirectiveBinding) => {
    let moveElement:HTMLElement = el as HTMLElement;
    const mouseDown = (e:MouseEvent) => {
        console.log(1111111111,e.clientX);
        console.log(2222222222,el.offsetLeft);
        
        
        let X = e.clientX  - el.offsetLeft
        let Y = e.clientY  - el.offsetTop
        console.log(e);
        const move = (e:MouseEvent) =>{
            el.style.left = e.clientX - X + 'px'
            el.style.top = e.clientY - Y + 'px'            
        }
        document.addEventListener("mousemove",move)
        document.addEventListener("mouseup",()=>{
            document.removeEventListener("mousemove",move)
        })
    }
    moveElement.addEventListener("mousedown",mouseDown)
    
    
}
</script>
 
<style scoped lang='less'>
 .container{
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 200px;
    height: 200px;
    border: 3px solid black;
    .header{
        height: 20px;
        background: black;
    }
    
 }
</style>