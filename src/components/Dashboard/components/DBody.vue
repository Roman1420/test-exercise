<template>
    <div class="d-body">
        <div class="d-body__filters">
            <div class="d-body__filters-button">
                <div class="d-body__filters-button-icon">
                    <icon-plus-circle/>
                </div>
                <span>Create new</span>
            </div>
            <div 
                :class="[{ 'active': currentFilter === filter.value}, 'd-body__filter']"
                v-for="filter in filtersList"
                :key="filter.value"
                @click="setCurrentFilter(filter.value)"
            >
                <div class="d-body__filter-icon">
                    <component :is="filter.icon"/>
                </div>
                <div class="d-body__filter-info">
                    <div class="d-body__filter-title">{{ filter.title }}</div>
                    <div class="d-body__filter-desc">{{ filter.desc }}</div>
                </div>
            </div>
        </div>
        <div class="d-body__wrapper">
            <div class="d-body__header">
                <div class="d-body__header-title">Dashboard</div>
                <div class="d-body__date">
                    <span>Aug 21, 2021 · Sep 21 2021</span>
                    <div class="d-body__date-button"></div>
                </div>
                <div class="d-body__header-button">
                    <icon-printer/>
                </div>
                <div class="d-body__header-button">
                    <icon-download/>
                </div>
            </div>
            <div class="d-body__table">
                <div class="d-body__table-heads">
                    <div class="d-body__table-head">Data</div>
                    <div class="d-body__table-head">Summary1</div>
                    <div class="d-body__table-head">Summary2</div>
                    <div class="d-body__table-head">Summary3</div>
                    <div class="d-body__table-head">Summary4</div>
                    <div class="d-body__table-head">Summary5</div>
                </div>
                <div class="d-body__table-list">
                    <div 
                        class="d-body__table-item"
                        v-for="item in listByFilterId"
                        :key="item.id"
                    >
                        <div class="d-body__table-name">{{ `Data${item.id}` }}</div>
                        <div class="d-body__table-summary">{{ item.summary1 }}</div>
                        <div class="d-body__table-summary">{{ item.summary2 }}</div>
                        <div class="d-body__table-summary">{{ item.summary3 }}</div>
                        <div class="d-body__table-summary">{{ item.summary4 }}</div>
                        <div class="d-body__table-summary">{{ item.summary5 }}</div>
                    </div>
                </div>
                <div class="d-body__search">
                    <input 
                        class="d-body__input"
                        placeholder="Search..."
                        v-model="filterById"
                    >
                    <input 
                        class="d-body__input"
                        v-model="filterBySummary1"
                    >
                    <input 
                        class="d-body__input"
                        v-model="filterBySummary2"
                    >
                    <input 
                        class="d-body__input"
                        v-model="filterBySummary3"
                    >
                    <input 
                        class="d-body__input"
                        v-model="filterBySummary4"
                    >
                    <input 
                        class="d-body__input"
                        v-model="filterBySummary5"
                    >
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import IconPlusCircle from '../../icons/IconPlusCircle.vue'
import IconCheckOutline from '../../icons/IconCheckOutline.vue'
import IconChartDonut from '../../icons/IconChartDonut.vue'
import IconPrint from '../../icons/IconPrint.vue'
import IconPrinter from '../../icons/IconPrinter.vue'
import IconDownload from '../../icons/IconDownload.vue'
export default {
    components: {
        IconPlusCircle,
        IconCheckOutline,
        IconChartDonut,
        IconPrint,
        IconPrinter,
        IconDownload,
    },
    data() {
        return {
            currentFilter: null,
            filterById: null,
            filterBySummary1: '',
            filterBySummary2: '',
            filterBySummary3: '',
            filterBySummary4: '',
            filterBySummary5: '',
            filtersList: [
                {
                    title: 'Even rows of data',
                    desc: 'Display rows 2,4,6 etc',
                    icon: 'IconChartDonut',
                    value: 'even',
                },
                {
                    title: 'Odd rows of data',
                    desc: 'Display rows 1,3,5 etc',
                    icon: 'IconCheckOutline',
                    value: 'odd',
                },
                {
                    title: 'All data',
                    desc: 'Display all data',
                    icon: 'IconPrint',
                    value: 'all',
                },
            ],
            list: [
                {
                    id: 1,
                    summary1: 186,
                    summary2: 186,
                    summary3: 92,
                    summary4: 8,
                    summary5: 1,
                },
                {
                    id: 2,
                    summary1: 95,
                    summary2: 95,
                    summary3: 31,
                    summary4: 11,
                    summary5: 0,
                },
                {
                    id: 3,
                    summary1: 329,
                    summary2: 329,
                    summary3: 256,
                    summary4: 32,
                    summary5: 4,
                },
                {
                    id: 4,
                    summary1: 804,
                    summary2: 804,
                    summary3: 697,
                    summary4: 42,
                    summary5: 40,
                },
                {
                    id: 5,
                    summary1: 176,
                    summary2: 149,
                    summary3: 2,
                    summary4: 99,
                    summary5: 111,
                },
                {
                    id: 45,
                    summary1: 804,
                    summary2: 804,
                    summary3: 697,
                    summary4: 42,
                    summary5: 40,
                },
            ]
        }
    },
    mounted() {
        this.currentFilter = this.filtersList[this.filtersList.length - 1].value
    },
    computed: {
        listByCurrentFilter() {
            if (!this.currentFilter || this.currentFilter === 'all') return this.list
            return this.list.filter(element => this.checkNumber(element.id))
        },
        listByFilterId() {
            if (this.filterById) return this.listByCurrentFilter.filter(element => String(element.id).toLowerCase().includes(String(this.filterById).toLowerCase()))
            return this.listByCurrentFilter
        }
    },
    methods: {
        checkNumber(number) {
            return this.currentFilter === 'even' 
                ? number % 2 === 0
                : number % 2 !== 0
        },
        setCurrentFilter(value) {
            this.currentFilter = value
        },
    },
}
</script>

<style lang="scss">
.d-body {
    display: flex;
    align-items: flex-start;
    background: #E2F0F0;
    width: 100%;
    gap: 6%;
    padding-top: 12px;
    padding-right: 120px;
    padding-bottom: 32px;
    padding-left: 64px;

    &__filters {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding-top: 20px;
        width: 20%;
        min-width: 20%;

        &-button {
            display: flex;
            align-items: center;
            justify-content: center;
            background: #FFFFFF;
            color: #367BF5;
            position: relative;
            cursor: pointer;
            border-radius: 99px;
            padding-right: 50px;
            padding-left: 50px;
            padding-bottom: 3px;
            height: 56px;
            gap: 8px;
            font-weight: 500;
            font-size: 20px;
            line-height: 28px;
            letter-spacing: 0.15px;
            box-shadow: 0px 6px 24px rgba(54, 123, 245, 0.06), 0px 6px 12px rgba(54, 123, 245, 0.06);
            margin-bottom: 24px;
            transition: .3s;

            &-icon {
                display: flex;
                position: absolute;
                pointer-events: none;
                left: 16px;
            }

            &:hover {
                box-shadow: 0px 16px 24px rgba(54, 123, 245, 0.16), 0px 6px 12px rgba(54, 123, 245, 0.16);
            }
        }
    }

    &__filter {
        display: flex;
        align-items: center;
        cursor: pointer;
        width: 100%;
        gap: 12px;
        padding: 7px 0 7px 12px;
        border-radius: 10px;
        transition: .3s;

        &.active {
            background: #E6EFFF;
        }

        &.active, &:hover {
            .d-body__filter-icon {
                svg {
                    path {
                        fill: #367BF5;
                    }
                }
            }
        }

        &-info {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
        }
        
        &-icon {
            svg {
                path {
                    fill: #78909C;
                    transition: .3s;
                }
            }
        }

        &-title {
            font-weight: 500;
            font-size: 16px;
            line-height: 24px;
            letter-spacing: 0.44px;
            color: rgba(0, 0, 0, 0.87);
        }

        &-desc {
            font-weight: 400;
            font-size: 12px;
            line-height: 16px;
            letter-spacing: 0.4px;
        }
    }

    &__wrapper {
        display: flex;
        flex-direction: column;
        width: 80%;
    }

    &__header {
        display: flex;
        align-items: center;
        gap: 8px;

        &-title {
            width: 100%;
            font-weight: 500;
            font-size: 34px;
            line-height: 42px;
            display: flex;
            align-items: center;
            letter-spacing: 0.25px;
            color: rgba(0, 0, 0, 0.87);
        }

        &-button {
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            min-width: 32px;
            width: 32px;
            height: 32px;
            background: #F7F9FA;
            border-radius: 4px;
        }
    }

    &__table {
        display: flex;
        flex-direction: column;

        &-heads {
            width: 100%;
        }

        &-heads, &-item {
            display: flex;
            align-items: center;
            width: inherit;
        }

        &-head, &-summary, &-name {
            border-bottom: 2px solid #E3E5E6;
        }

        &-head, &-summary {
            width: 13%;
            font-size: 16px;
            line-height: 24px;
            letter-spacing: 0.44px;
            text-align: right;
        }

        &-head:first-child, &-name{
            text-align: left;
            width: 35%;
        }

        &-head {
            display: flex;
            align-items: center;
            justify-content: flex-end;
            height: 48px;

            &:first-child {
                justify-content: flex-start;
            }
        }

        &-name, &-summary {
            display: flex;
            align-items: center;
            height: 65px;
            font-weight: 500;
        }

        &-name {
            color: rgba(0, 0, 0, 0.87);
        }

        &-item {
            font-size: 20px;
            line-height: 28px;
            letter-spacing: 0.15px;

            &:last-child {
                .d-body__table {
                    &-name, &-summary {
                        border-bottom: none;
                    }
                }
            }
        }

        &-summary {
            justify-content: flex-end;
        }

        &-list {
            display: flex;
            flex-direction: column;
            overflow-y: auto;
            height: 256px;
            min-height: 256px;

            &::-webkit-scrollbar {
                width: 0;
                display: none;
            }
        }
    }

    &__date {
        display: flex;
        align-items: center;
        height: 32px;
        border: 1px solid #C6CACC;
        border-radius: 10px;
        padding-left: 12px;
        padding-right: 12px;

        span {
            width: max-content;
        }
    }

    &__search {
        display: grid;
        grid-template-columns: 35% auto auto auto auto auto;
        align-items: center;
        gap: 3%;
    }

    &__input {
        outline: none;
        background-color: transparent;
        border: 1px solid #C6CACC;
        border-radius: 10px;
        height: 32px;
        width: 100%;
        padding-left: 12px;
        min-width: -webkit-fill-available;
    }
}
</style>
