<template>
    <div class="directions-wrapper">
        <div class="container">
            <div class="title" v-if="$props?.title">{{ $props.title }}</div>
            <div class="items">
                <div v-for="item in $props.items" class="item pointerable">
                    <div class="left" v-if="item?.title">
                        <div class="title">
                            {{ item.title }}
                        </div>
                    </div>
                    <div class="right"  v-if="item?.text">
                        <div class="square" />
                        <div class="text">
                            {{ item.text }}
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ListDirections',
    props: {
        title: {
            required: false,
            type: String
        },
        items: {
            required: true,
            type: Array
        }
    }
}
</script>

<style scoped lang="scss">
.directions-wrapper {
    background: #000;
    padding-top: 60px;
    padding-bottom: 60px;
}
.title {
    font-weight: 700;
    font-size: 40px;
    line-height: 100%;
    letter-spacing: 0%;
    text-transform: uppercase;
    margin-bottom: 60px;
    color: #fff;
}
@keyframes slide-gradient-left {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(0%);
  }
}

@keyframes slide-gradient-right {
  0% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(0%);
  }
}
.items {
    .item {
        position: relative;
        overflow: hidden; // чтобы не вылезал градиент
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 40px;
        border-bottom: 1px solid #465DB699;

        &::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, rgba(20, 110, 245, 0.05) 0%, rgba(20, 110, 245, 0.4) 100%);
            z-index: 0;
            opacity: 0;
            transform: translateX(-100%);
            transition: transform 1s ease, opacity 0.5s ease;
        }
        
        &:hover::before {
            opacity: 1;
            transform: translateX(0%);
        }

        &:nth-child(even)::before {
            background: linear-gradient(270deg, rgba(20, 110, 245, 0.05) 0%, rgba(20, 110, 245, 0.4) 100%);
            transform: translateX(100%);
        }

        &:nth-child(even):hover::before {
            transform: translateX(0%);
            opacity: 1;
        }

        &:nth-child(even) {
            flex-direction: row-reverse;
            margin-right: 15px;
        }
        .left, .right {
            position: relative;
            z-index: 1;
        }
        .left {
            .title {
                font-weight: 700;
                font-size: 70px;
                line-height: 100%;
                letter-spacing: 0%;
                text-transform: uppercase;
                color: #fff;
                transition: 0.25s;
            }
        }
        .right {
            max-width: 660px;

            .square {
                background: #D9D9D9;
                width: 10px;
                max-width: 10px;
                height: 10px;
                margin-bottom: 30px;
            }
            .text {
                font-weight: 400;
                font-size: 16px;
                line-height: 20px;
                letter-spacing: 0%;
                color: #fff;
                text-align: justify;              // Растягивает строки по ширине блока
                text-justify: inter-word;         // Управляет тем, как происходит выравнивание
            }
        }
        &:hover {
            .left {
                .title {
                    color: #146EF5;
                }
            }
        }
    }
}
</style>