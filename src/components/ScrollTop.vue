<template>
    <div
        v-show="showGoTopIcon"
        id="goToTop"
        class='go-to-top'
        @click="scrollToTop"
    >
        <img src="../assets/backtotop.png">
    </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator';

@Component({
    components: {},
})
export default class ScrollTop extends Vue {
    private showGoTopIcon: boolean = false;
    private scrollTop: number = 0;
    private goTopSrc: string = './assets/backtotop.png';

    //////////////////// Vue Life ////////////////////
    private async beforeCreate() {}
    private async created() {}
    private async beforeMount() {}
    private async mounted() {
        this.$nextTick(() => window.addEventListener('scroll', this.showScrollToTopIcon, true));
    }
    private async beforeDestroy() {}
    private async destroyed() {
        window.removeEventListener('scroll', this.showScrollToTopIcon, true);
    }

    private scrollToTop(): void {
        const that = this;
        let timer = setInterval(() => {
            let ispeed = Math.floor(-that.scrollTop / 5);
            document.documentElement.scrollTop = document.body.scrollTop = that.scrollTop + ispeed;
            if (that.scrollTop === 0) {
                clearInterval(timer);
            }
        }, 16);
    }

    // 計算距離頂部的高度，當高度大於60顯示回頂部圖標，小於60則隱藏
    private showScrollToTopIcon(): void {
        const that = this;
        let scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
        that.scrollTop = scrollTop;
        if (that.scrollTop > 60) {
            that.showGoTopIcon = true;
        } else {
            that.showGoTopIcon = false;
        }
    }
}
</script>

<style lang="scss" scoped>
.go-to-top {
    cursor: pointer;

    position: fixed;
    bottom: 5rem;
    right: 1.4rem;
    z-index: 999;
}
</style>