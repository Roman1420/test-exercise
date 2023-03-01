<template>
    <div class="d-header">
        <div class="d-header__logo">
            <icon-logo/>
        </div>
        <div class="d-header__help">
            Help
            <icon-question-mark/>
        </div>
        <div class="d-header__button">upgrade</div>
        <div 
            class="d-header__avatar"
            :style="{ backgroundImage: 'url(/src/assets/images/' + avatar + ')' }"
        ></div>
    </div>
</template>

<script>
import IconLogo from '../../icons/IconLogo.vue'
import IconQuestionMark from '../../icons/IconQuestionMark.vue'
export default {
    name: 'DHeader',
    components: {
        IconLogo,
        IconQuestionMark,
    },
    data() {
        return {
            avatar: 'Fernando_Pidrilio.png'
        }
    }
}
</script>

<style lang="scss">
.d-header {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    position: relative;
    gap: 16px;
    padding: 12px 16px;

    &__logo {
        position: absolute;
        pointer-events: none;
        left: 16px;
        top: 12px;
    }

    &__help {
        display: flex;
        align-items: center;
        justify-content: space-between;
        background: #F7F9FA;
        cursor: pointer;
        height: 40px;
        border-radius: 10px;
        padding-left: 9px;
        padding-right: 8px;
        min-width: 96px;
        font-weight: 400;
        font-size: 16px;
        line-height: 24px;
        letter-spacing: 0.44px;
    }

    &__button {
        display: flex;
        align-items: center;
        text-align: center;
        text-transform: uppercase;
        color: #367BF5;
        cursor: pointer;
        font-weight: 500;
        font-size: 14px;
        line-height: 16px;
        letter-spacing: 0.75px;
        height: 40px;
        padding-left: 9px;
        padding-right: 9px;
        border-radius: 10px;
        box-shadow: 0px 4px 8px rgba(54, 123, 245, 0.16), 0px 2px 4px rgba(54, 123, 245, 0.04);
        transition: .3s;

        &:hover {
            box-shadow: 0px 4px 8px rgba(54, 123, 245, 0.16), 0px 2px 4px rgba(54, 123, 245, 0.24);
        }
    }

    &__avatar {
        background-size: contain;
        background-repeat: no-repeat;
        background-position: center;
        overflow: hidden;
        background: #FFFFFF;
        width: 40px;
        height: 40px;
        border-radius: 50%;
    }
}
</style>
