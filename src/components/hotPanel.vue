<template>
    <a href="#">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <div class="hotPanel">
            <hotButton
                :hotButton="{ title: 'Sport' }"
                @hotSearch="onHotSearch"
            />
            <hotButton
                :hotButton="{ title: 'Weather' }"
                @hotSearch="onHotSearch"
            />
            <hotButton
                :hotButton="{ title: 'Culture' }"
                @hotSearch="onHotSearch"
            />
            <hotButton
                :hotButton="{ title: 'Politics' }"
                @hotSearch="onHotSearch"
            />
            <hotButton
                :hotButton="{ title: 'Travell' }"
                @hotSearch="onHotSearch"
            />
            <hotButton
                :hotButton="{ title: 'Business' }"
                @hotSearch="onHotSearch"
            />
            <hotButton
                :hotButton="{ title: 'Health' }"
                @hotSearch="onHotSearch"
            />
            <hotButton
                :hotButton="{ title: 'Future' }"
                @hotSearch="onHotSearch"
            />
            <hotButton
                :hotButton="{ title: 'Tech' }"
                @hotSearch="onHotSearch"
            />
            <hotButton
                :hotButton="{ title: 'World' }"
                @hotSearch="onHotSearch"
            />
        </div>
    </a>
</template>
<script>
import hotButton from "./hotButton.vue";
export default {
    name: "hotPanel",
    components: {
        hotButton,
    },
    // watch: {
    //     hotSearch: 'onHotSearch'
    // },
    methods: {
        onHotSearch(data) {
            this.$emit("hotSearch", data);
        },
    },
};
</script>
<style>
.hotPanel {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    height: 50px;
    width: 94vw;
}

.hotPanel button {
    width: 140px;
    height: 40px;
    border-radius: 10px;
    cursor: pointer;
    font-weight: 700;
    font-size: 20px;
}

.hotPanel button:hover {
    color: brown;
}
a {
    transform: translate(0%, 0%);
    color: #1670f0;
    padding: 30px;
    letter-spacing: 2px;
    text-transform: uppercase;
    text-decoration: none;
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
    overflow: hidden;
}
a:before {
    content: "";
    top: 2px;
    left: 2px;
    bottom: 2px;
    width: 50%;
    background: rgba(255, 255, 255, 0.05);
}
a span:nth-child(1) {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 2px;
    background: linear-gradient(to right, #0c002b, #1779ff);
    animation: animate1 2s linear infinite;
}
@keyframes animate1 {
    0% {
        transform: translateX(-100%);
    }
    100% {
        transform: translateX(100%);
    }
}
a span:nth-child(2) {
    position: absolute;
    top: 0;
    right: 0;
    width: 2px;
    height: 100%;
    background: linear-gradient(to bottom, #0c002b, #1779ff);
    animation: animate2 2s linear infinite;
    animation-delay: 1s;
}
@keyframes animate2 {
    0% {
        transform: translateY(-100%);
    }
    100% {
        transform: translateY(100%);
    }
}
a span:nth-child(3) {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 2px;
    background: linear-gradient(to left, #0c002b, #1779ff);
    animation: animate3 2s linear infinite;
}
@keyframes animate3 {
    0% {
        transform: translateX(100%);
    }
    100% {
        transform: translateX(-100%);
    }
}
a span:nth-child(4) {
    position: absolute;
    top: 0;
    left: 0;
    width: 2px;
    height: 100%;
    background: linear-gradient(to top, #0c002b, #1779ff);
    animation: animate4 2s linear infinite;
    animation-delay: 1s;
}
@keyframes animate4 {
    0% {
        transform: translateY(100%);
    }
    100% {
        transform: translateY(-100%);
    }
}
</style>
