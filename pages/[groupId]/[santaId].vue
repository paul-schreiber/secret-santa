<template>
    <div class="h-screen w-screen flex flex-col items-center bg-black text-white">
        <div
            class="w-4/5 h-60 rounded-xl drop-shadow-lg absolute bottom-40 bg-gray-200 z-10 p-8 text-xl text-center text-black">
            <p>Hallo {{ santaName }},</p>
            <p></p>
            <p>Du darfst dieses Jahr ein Geschenk für folgende Person besorgen:</p>
            <strong>{{ presentee }}</strong>
            <p>Viel Spaß beim Wichteln!</p>
        </div>
        <div class="canvas">
            <div class="snowing">
                <div class="small-snow">
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                    <div class="small"></div>
                </div>
                <div class="medium-snow">
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                    <div class="medium"></div>
                </div>
            </div>
            <div class="tree"></div>
            <div class="tree"></div>
            <div class="tree"></div>
            <div class="tree"></div>
            <div class="tree"></div>
            <div class="tree"></div>
            <div class="tree"></div>
            <div class="tree"></div>
            <div class="tree"></div>
            <div class="tree"></div>
            <div class="tree"></div>
            <div class="tree"></div>
            <div class="tree-parts">
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
                <div class="tree-part"></div>
            </div>
            <div class="house">
                <div class="front">
                    <div class="a"></div>
                    <div class="b"></div>
                    <div class="c"></div>
                    <div class="d"></div>
                    <div class="e"></div><span class="f"></span><span class="f"></span><span class="f"></span><span
                        class="f"></span><span class="f"></span><span class="f"></span>
                    <div class="g"></div>
                    <div class="k"></div>
                </div>
                <div class="side">
                    <div class="wall-snow"></div>
                    <div class="w-area">
                        <div class="w-outer"></div>
                        <div class="window">
                            <div class="w-inner"></div>
                            <div class="w-shadow"></div>
                        </div>
                    </div>
                    <div class="w-area">
                        <div class="w-outer"></div>
                        <div class="window">
                            <div class="w-inner"></div>
                            <div class="w-shadow"></div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="ground-d"></div>
            <div class="ground-a"></div>
            <div class="ground-b"></div>
            <div class="ground-c"></div>
        </div>

    </div>
</template>


<script lang="ts" setup>
import { computed, ref } from "vue";
import serverConfig from "@/server-config";
const route = useRoute()
const presentee = ref('')
const groupId = ref(route.params.groupId)
const santaId = ref(route.params.santaId)
const santaName = ref('')

fetch(`${serverConfig.serverURL}/${groupId.value}/${santaId.value}`).then(async res => {
    const { name, presenteeName } = await res.json()
    presentee.value = presenteeName
    santaName.value = name
})

</script>

<style lang="scss">
.canvas {
    width: 100%;
    height: 100%;
    max-width: 900px;
    max-height: 900px;
    overflow: hidden;
    position: relative;
    background-color: #aeebdd;
    border-radius: 6px;
    box-shadow: 0px 0px 52px -10px rgba(23, 102, 90, 1);
}

.house {
    position: absolute;
    left: 130px;
    bottom: 40px;
    height: 370px;
    z-index: 1;
}

.front {
    clip-path: polygon(50% 0%, 5% 100%, 95% 100%);
    height: 370px;
    width: 280px;
    background-color: #77545c;
    position: absolute;
    left: 0;
    top: 0;
}

.front:before {
    width: 170px;
    position: absolute;
    left: 41px;
    height: 17px;
    content: "";
    z-index: 1;
    bottom: 0;
    background-color: #e3e7ec;
    transform: skew(-60deg);
}

.front .a {
    clip-path: polygon(61% 0px, 53.82% 72.15%, 0px 100%, 53% 0px);
    transform: rotate(-3deg);
    background-color: #583642;
    position: absolute;
    left: 16px;
    top: 0;
    width: 100%;
    height: 100%;
}

.front .b {
    clip-path: polygon(61.70% 3px, 8.28% 104.6%, -11px 101.62%, 44.48% -6px);
    background-color: #77545c;
    position: absolute;
    right: -9px;
    transform: rotateY(-147deg);
    top: 0;
    height: 100%;
    width: 100%;
    z-index: 2;
}

.front .c {
    clip-path: polygon(53.87% 20.38%, 18% 100%, 86.29% 99.73%);
    height: 370px;
    width: 280px;
    background-color: #8e4940;
    position: absolute;
    top: 0;
    left: 0;
}

.front .f {
    position: absolute;
    width: 20px;
    height: 20px;
    background-color: #a95b41;
    z-index: 2;
    left: 150px;
    bottom: 0;
    border-radius: 50%;
    box-shadow: 0 0 0 3px #a95b41 inset, 0 0 0 4px rgba(65, 10, 34, 0.25) inset;

    &:after {
        content: "";
        position: absolute;
        border: 1px solid rgba(65, 10, 34, 0.25);
        border-radius: 50%;
        width: 9px;
        height: 9px;
        left: 5px;
        top: 5px;
    }

    &:before {
        content: "";
        position: absolute;
        border: 1px solid rgba(65, 10, 34, 0.25);
        border-radius: 50%;
        width: 5px;
        height: 5px;
        left: 7px;
        top: 7px;
    }

    &:nth-of-type(2) {
        left: 170px;
    }

    &:nth-of-type(3) {
        left: 190px;
    }

    &:nth-of-type(4) {
        left: 180px;
        bottom: 16px;
    }

    &:nth-of-type(5) {
        left: 160px;
        bottom: 16px;
    }

    &:nth-of-type(6) {
        left: 170px;
        bottom: 33px;
    }
}

.front .g {
    position: absolute;
    width: 100px;
    height: 52px;
    bottom: 0;
    left: 170px;
    background-color: #410a22;
    z-index: 1;
    transform: skew(-30deg);
}

.front .e {
    position: absolute;
    bottom: 12px;
    z-index: 1;
    left: 122px;
    width: 42px;
    border-left: 10px solid;
    border-top: 10px solid;
    border-right: 10px solid;
    border-color: #9b5642;
    height: 110px;
    background-color: #69424d;
    box-shadow: 4px 4px 0 0 #4d323e inset, 2px 0 0 #7d402f;
}

.front .e:after,
.front .e:before {
    content: "";
    position: absolute;
    left: 10px;
    width: 10px;
    height: 38px;
    background-color: rgba(#4d323e, .45);
    box-shadow: 15px 0 0 0 rgba(#4d323e, .45);
}

.front .e:after {
    top: 10px;
}

.front .e:before {
    top: 60px;
}

.front .k {
    position: absolute;
    border: 2px solid #4d323e;
    width: 40px;
    height: 60px;
    top: 150px;
    left: 132px;
    background: linear-gradient(118deg, rgba(225, 150, 96, 1) 12%, rgba(253, 213, 141, 1) 65%);
    box-shadow: 2px 2px 0 inset #8f4b41;

    &:after {
        content: "";
        position: absolute;
        width: 100%;
        height: 2px;
        top: 14px;
        left: 0;
        background-color: #4d323e;
        box-shadow: 0 16px 0 #4d323e, 0 32px 0 #4d323e;
    }

    &:before {
        content: "";
        position: absolute;
        width: 2px;
        height: 100%;
        top: 0;
        left: calc(50% - 1px);
        background-color: #4d323e;
    }
}

.side {
    position: absolute;
    width: 460px;
    height: 370px;
    clip-path: polygon(20px 1px, 67.61% 5px, 100% 100%, 31.53% 100.54%);
    top: 0;
    left: 120px;
    background: linear-gradient(200deg, rgba(187, 46, 45, 1) 12%, rgba(122, 52, 60, 1) 98%);

    &:after {
        content: "";
        position: absolute;
        height: 100%;
        width: 2px;
        color: #e4a06880;
        background-color: currentColor;
        left: 140px;
        top: 0;
        transform: skew(20deg);
        box-shadow: 6px 0 0, 60px 0 0, 66px 0 0, 120px 0 0, 126px 0 0, 180px 0 0, 186px 0 0;
        z-index: -1;
    }

    &:before {
        content: "";
        position: absolute;
        width: 100%;
        height: 20px;
        background: #b1302f;
    }
}

.window {
    position: absolute;
    left: 129px;
    top: 80px;
    clip-path: polygon(50% 30%, 0% 100%, 100% 100%);
    background-color: #5c3944;
    width: 60px;
    height: 60px;
    z-index: 2;
}

.w-inner {
    position: absolute;
    width: 100%;
    height: 100%;
    content: "";
    background: linear-gradient(118deg, #e19660 47%, #fdd58d 65%);
    right: 3px;
    top: 0;
    clip-path: polygon(50% 30%, 0% 100%, 100% 100%);

    &:after {
        content: "";
        width: 100%;
        height: 3px;
        background-color: #5c3944;
        position: absolute;
        top: 41px;
        left: 0;
    }

    &:before {
        content: "";
        width: 3px;
        height: 100%;
        background-color: #5c3944;
        position: absolute;
        top: 0;
        left: 50%;
    }
}

.w-shadow {
    position: absolute;
    left: -62%;
    top: 0;
    width: 100%;
    height: 100%;
    transform: rotate(25deg);
    background-color: rgba(0, 0, 0, .15);
}

.w-outer {
    position: absolute;
    top: 70px;
    left: 124px;
    width: 70px;
    height: 70px;
    clip-path: polygon(50% 30%, 0% 100%, 100% 100%);
    background: #955853;
}

.w-area:before {
    position: absolute;
    left: 100px;
    top: 80px;
    height: 70px;
    width: 60px;
    clip-path: polygon(16px 51.85%, 46.99% 17px, 98.33% 11px, 40.67% 85.71%);
    content: "";
    background: linear-gradient(0deg, #611e22 0%, #ab2c2a 100%);
}

.w-area:nth-child(2) {
    position: absolute;
    left: 120px;
}

.ground-a {
    position: absolute;
    left: -100px;
    bottom: -70px;
    width: 280px;
    height: 180px;
    border-radius: 40%;
    background-color: #f6f5ff;
    transform: rotate(25deg);
    z-index: 2;

    &:after {
        content: "";
        position: absolute;
        left: -20px;
        top: 20px;
        width: 160px;
        height: 100px;
        transform: rotate(-25deg);
        background-color: #fff;
        border-radius: 50%;
    }
}

.ground-b {
    position: absolute;
    left: 400px;
    bottom: -80px;
    height: 160px;
    width: 250px;
    background-color: #fff;
    z-index: 1;
    transform: scaleX(1.2) skewx(20deg);
    border-radius: 80% 25%;
}

.ground-c {
    position: absolute;
    left: 300px;
    bottom: -70px;
    height: 120px;
    width: 200px;
    background-color: #edf1f7;
    z-index: 1;

    border-radius: 80% 65%;
}

.ground-d {
    position: absolute;
    bottom: -8px;
    left: 0;
    width: 100%;
    height: 50px;
    background-color: #f6f5ff;
    z-index: 1;
}

.tree {
    position: absolute;
    clip-path: polygon(50% 0%, 15% 100%, 88% 100%);
    width: 300px;
    height: 700px;

    &:nth-child(1) {
        background-color: #17665a;
        top: -160px;
        left: -114px;
    }

    &:nth-child(2) {
        background-color: #024b41;
        top: -100px;
        left: -60px;
        z-index: 1;
    }

    &:nth-child(3) {
        background-color: #339580;
        top: 50px;
        left: 40px;
    }

    &:nth-child(4) {
        background-color: #1c6f61;
        top: -100px;
        left: 170px;
        z-index: 1;
    }

    &:nth-child(5) {
        background-color: #339580;
        top: -20px;
        left: 240px;
        z-index: 0;
    }

    &:nth-child(6) {
        background-color: #339580;
        top: -20px;
        left: 460px;
    }

    &:nth-child(7) {
        background-color: #17665a;
        top: 120px;
        left: 560px;
    }

    &:nth-child(8) {
        background-color: #024b41;
        top: 300px;
        left: 510px;
        z-index: 3;
        width: 400px;
    }

    &:nth-child(9) {
        background-color: #024b41;
        top: 440px;
        left: 360px;
        z-index: 3;
        width: 500px;
    }

    &:nth-child(10) {
        background-color: #0c332d;
        top: 300px;
        left: 560px;
        z-index: 3;
        width: 500px;
    }

    &:nth-child(11) {
        background-color: #26816f;
        top: 0px;
        left: 640px;
    }

    &:nth-child(12) {
        background-color: #26816f;
        top: -40px;
        left: -150px;
    }
}

.snowing {
    position: absolute;
    filter: blur(.8px);
    z-index: 3;
    width: 100%;
    height: 100%;
}

.snowing .small {
    position: absolute;
    width: 6px;
    height: 6px;
    background: #fff;
    border-radius: 50%;
    animation-name: snow-fall, snow-shake;
    animation-duration: 12s, 4s;
    animation-timing-function: linear, ease-in-out;
    animation-iteration-count: infinite, infinite;
    top: -100%;

    &:nth-child(1) {
        left: 210px;
        top: -40px;
        animation-delay: 9s, .3s;
    }

    &:nth-child(2) {
        left: 400px;
        top: -50px;
        animation-delay: 6s, .3s;
    }

    &:nth-child(3) {
        left: 720px;
        top: -130px;
        animation-delay: 8s, .3s;
    }

    &:nth-child(4) {
        left: 140px;
        animation-delay: 10s, .3s;
    }

    &:nth-child(5) {
        left: 500px;
        animation-delay: 7s, .2s;
    }

    &:nth-child(6) {
        left: 150px;
        top: -30px;
        animation-delay: 5.2s, .3s;
    }

    &:nth-child(7) {
        left: 200px;
        top: -20px;
        animation-delay: 3.4s, .3s;
    }

    &:nth-child(8) {
        left: 70px;
        top: -330px;
        animation-delay: 6.6s, .3s;
    }

    &:nth-child(9) {
        left: 380px;
        top: -90px;
        animation-delay: 5.6s, .3s;
    }

    &:nth-child(10) {
        left: 130px;
        animation-delay: 11s, .2s;
    }

    &:nth-child(11) {
        left: 20px;
        animation-delay: 10.5s, .3s;
    }

    &:nth-child(12) {
        left: 620px;
        top: -40px;
        animation-delay: 8s, .3s;
    }

    &:nth-child(13) {
        left: 400px;
        top: -180px;
        animation-delay: 3.7s, 3s;
    }

    &:nth-child(14) {
        left: 500px;
        top: -370px;
        animation-delay: 6s, .3s;
    }

    &:nth-child(15) {
        left: 660px;
        top: -20px;
        animation-delay: 9s, .3s;
    }

    &:nth-child(16) {
        left: 610px;
        top: -80px;
        animation-delay: 7.3s, .3s;
    }

    &:nth-child(17) {
        left: 20px;
        top: -210px;
        animation-delay: 6.8s, 2s;
    }

    &:nth-child(18) {
        left: 670px;
        top: -200px;
        animation-delay: 6.5s, .6s;
    }

    &:nth-child(19) {
        left: 210px;
        top: -120px;
        animation-delay: 4s, .3s;
    }

    &:nth-child(20) {
        left: 20px;
        top: -110px;
        animation-delay: -1.1s, -.1s;
    }
}

.snowing .medium {
    position: absolute;
    width: 8px;
    height: 8px;
    background: #fff;
    border-radius: 50%;
    animation-name: snow-fall, snow-shake;
    animation-duration: 12s, 4s;
    animation-timing-function: linear, ease-in-out;
    animation-iteration-count: infinite, infinite;
    top: -100%;

    &:nth-child(1) {
        left: 300px;
        top: -420px;
        animation-delay: 3.4s, 1s;
    }

    &:nth-child(2) {
        left: 530px;
        animation-delay: .2s, .1s;
    }

    &:nth-child(3) {
        left: 340px;
        top: -110px;
        animation-delay: 6s, 2s;
    }

    &:nth-child(4) {
        left: 250px;
        top: -390px;
        animation-delay: 3.4s, 3s;
    }

    &:nth-child(5) {
        left: 400px;
        top: -150px;
        animation-delay: 8.4s, .3s;
    }

    &:nth-child(6) {
        left: 720px;
        top: -240px;
        animation-delay: 7.7s, 1s;
    }

    &:nth-child(7) {
        left: 350px;
        top: -180px;
        animation-delay: 6s, 0.5s;
    }

    &:nth-child(8) {
        left: 560px;
        animation-delay: 1s, 0.5s;
    }

    &:nth-child(9) {
        left: 10px;
        top: -310px;
        animation-delay: 8.2s, 0.5s;
    }

    &:nth-child(10) {
        left: 40px;
        top: -220px;
        animation-delay: 3s, 1s;
    }

    &:nth-child(11) {
        left: 220px;
        top: -530px;
        animation-delay: .6s, 3s;
    }

    &:nth-child(12) {
        left: 630px;
        top: -10px;
        animation-delay: 9.4s, 2s;
    }

    &:nth-child(13) {
        left: 420px;
        top: -60px;
        animation-delay: 8s, 3s;
    }

    &:nth-child(14) {
        left: 580px;
        animation-delay: 2s, .3s;
    }

    &:nth-child(15) {
        left: 420px;
        top: -180px;
        animation-delay: 7s, 1s;
    }

    &:nth-child(16) {
        left: 360px;
        animation-delay: 8s, .3s;
    }

    &:nth-child(17) {
        left: 90px;
        top: -190px;
        animation-delay: 4.5s, 1s;
    }

    &:nth-child(18) {
        left: 130px;
        top: -330px;
        animation-delay: 8.2s, 1s;
    }

    &:nth-child(19) {
        left: 150px;
        top: -490px;
        animation-delay: 6.5s, .1s;
    }

    &:nth-child(20) {
        left: 640px;
        top: -270px;
        animation-delay: 10s, 1.5s;
    }
}

@keyframes snow-fall {
    0% {
        top: -10%;
    }

    100% {
        top: 100%;
    }
}

@keyframes snow-shake {
    0% {
        transform: translateX(0px);
    }

    50% {
        transform: translateX(60px);
    }

    100% {
        transform: translateX(0px);
    }
}

.wall-snow {
    position: absolute;
    background-color: #f9f8ff;
    width: 100%;
    height: 40px;
    top: 20px;

    &:before {
        content: "";
        position: absolute;
        width: 120px;
        height: 80px;
        border-radius: 50%;
        background-color: #f9f8ff;
        top: 0px;
        left: 40px;
    }

    &:after {
        content: "";
        position: absolute;
        width: 200px;
        height: 70px;
        border-radius: 50%;
        background-color: #f9f8ff;
        top: 0px;
        left: 140px;
        transform: rotate(-2deg);
    }
}

.tree-part {
    position: absolute;
    clip-path: polygon(33% 0, 0% 100%, 100% 24%);
    width: 28px;
    height: 24px;
    z-index: 3;

    &:nth-child(1) {
        top: 300px;
        left: 20px;
        background-color: #26816f;
    }

    &:nth-child(2) {
        top: 100px;
        left: 46px;
        background-color: #aeebdd;
    }

    &:nth-child(3) {
        top: 180px;
        left: 154px;
        background-color: #aeebdd;
    }

    &:nth-child(4) {
        top: 120px;
        left: 274px;
        background-color: #aeebdd;
    }

    &:nth-child(5) {
        top: 100px;
        left: 358px;
        background-color: #aeebdd;
    }

    &:nth-child(6) {
        top: 180px;
        left: 570px;
        background-color: #aeebdd;
    }

    &:nth-child(7) {
        top: 90px;
        left: 576px;
        background-color: #aeebdd;
    }

    &:nth-child(8) {
        top: 220px;
        left: 680px;
        background-color: #aeebdd;
    }

    &:nth-child(9) {
        top: 280px;
        left: 670px;
        background-color: #aeebdd;
    }

    &:nth-child(10) {
        top: 380px;
        left: 660px;
        background-color: #339580;
    }

    &:nth-child(11) {
        top: 420px;
        left: 674px;
        background-color: #17665a;
    }

    &:nth-child(12) {
        top: 360px;
        left: 680px;
        background-color: #17665a;
    }

    &:nth-child(13) {
        top: 360px;
        left: 680px;
        background-color: #17665a;
    }

    &:nth-child(14) {
        top: 200px;
        left: 750px;
        background-color: #aeebdd;
    }

    &:nth-child(15) {
        top: 110px;
        left: 760px;
        background-color: #aeebdd;
    }

    &:nth-child(16) {
        top: 340px;
        left: 730px;
        background-color: #17665a;
    }

    &:nth-child(17) {
        top: 440px;
        left: 760px;
        background-color: #26816f;
    }

    &:nth-child(18) {
        top: 150px;
        left: 410px;
        background-color: #aeebdd;
        transform: rotate(180deg);
    }

    &:nth-child(19) {
        top: 70px;
        left: 336px;
        background-color: #aeebdd;
        transform: rotate(180deg);
    }

    &:nth-child(20) {
        top: 130px;
        left: 120px;
        background-color: #aeebdd;
        transform: rotate(180deg);
    }

    &:nth-child(21) {
        top: 330px;
        left: 146px;
        background-color: #339580;
        transform: rotate(180deg);
    }

    &:nth-child(22) {
        top: 260px;
        left: 210px;
        background-color: #aeebdd;
        transform: rotate(180deg);
    }

    &:nth-child(23) {
        top: 260px;
        left: 644px;
        background-color: #aeebdd;
        transform: rotate(180deg);
    }

    &:nth-child(24) {
        top: 120px;
        left: 620px;
        background-color: #aeebdd;
        transform: rotate(180deg);
    }
}
</style>
