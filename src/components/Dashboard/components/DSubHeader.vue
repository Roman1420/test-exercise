<template>
    <div class="d-subheader">
        <div class="d-subheader__wrapper">
            <div class="d-subheader__item active">Analyze</div>
            <div class="d-subheader__item">My campaigns</div>
            <div class="d-subheader__item">Configure</div>
        </div>
    </div>
</template>

<style lang="scss">
.d-subheader {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;

    &__wrapper {
        display: flex;
        align-items: flex-end;
        min-width: 47%;
        z-index: 1;
    }

    &:after {
        content: '';
        position: absolute;
        pointer-events: none;
        border-bottom: 1px dashed #E3E5E6;
        left: 0;
        bottom: 0;
        right: 0;
        z-index: 0;
    }

    &__item {
        display: flex;
        align-items: center;
        text-align: center;
        cursor: pointer;
        padding: 16px 11px;
        font-weight: 400;
        font-size: 16px;
        line-height: 24px;
        letter-spacing: 0.44px;
        transition: .3s;

        &:hover {
            color: rgba(0, 0, 0, 0.87);
        }

        &.active {
            background-color: #fff;
            border: 1px solid #C6CACC;
            border-bottom: none;
            border-radius: 4px 4px 0px 0px;
            color: rgba(0, 0, 0, 0.87);
        }
    }
}
</style>
