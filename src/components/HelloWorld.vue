<template>
    <div class="hello">
        <h1>{{ msg }}</h1>

        <div id="app">
            <form action="" v-cloak id="main">
                <div class="bar">
                    <label>
                        <input type="text" v-model="searchString" placeholder="Enter your search terms">
                    </label>
                </div>
                <ul>
                    <li v-for="article in filteredArticle" :key="article.id">
                        <a :href="article.url">
                            <img :src="article.image" alt="">
                            <p>{{ article.title}}</p>
                        </a>
                    </li>
                </ul>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        data: function () {
            return {
                searchString: '',
                articles: [
                    {
                        title: "What You Need To Know About CSS Variables",
                        url: "https://tutorialzine.com/2016/03/what-you-need-to-know-about-css-variables/",
                        image: "https://tutorialzine.com/media/2016/03/css-variables.jpg"
                    },
                    {
                        title: "Freebie: 4 Great Looking Pricing Tables",
                        url: "https://tutorialzine.com/2016/02/freebie-4-great-looking-pricing-tables/",
                        image: "https://tutorialzine.com/media/2016/02/great-looking-pricing-tables.jpg"
                    },
                    {
                        title: "20 Interesting JavaScript and CSS Libraries for February 2016",
                        url: "https://tutorialzine.com/2016/02/20-interesting-javascript-and-css-libraries-for-february-2016/",
                        image: "https://tutorialzine.com/media/2016/02/interesting-resources-february.jpg"
                    },
                    {
                        title: "Quick Tip: The Easiest Way To Make Responsive Headers",
                        url: "https://tutorialzine.com/2016/02/quick-tip-easiest-way-to-make-responsive-headers/",
                        image: "https://tutorialzine.com/media/2016/02/quick-tip-responsive-headers.png"
                    },
                    {
                        title: "Learn SQL In 20 Minutes",
                        url: "https://tutorialzine.com/2016/01/learn-sql-in-20-minutes/",
                        image: "https://tutorialzine.com/media/2016/01/learn-sql-20-minutes.png"
                    },
                    {
                        title: "Creating Your First Desktop App With HTML, JS and Electron",
                        url: "https://tutorialzine.com/2015/12/creating-your-first-desktop-app-with-html-js-and-electron/",
                        image: "https://tutorialzine.com/media/2015/12/creating-your-first-desktop-app-with-electron.png"
                    }
                ]
            }
        },
        computed: {
            filteredArticle: function () {
                let article_array = this.articles,
                    searchString = this.searchString;
                if (!searchString) {
                    return article_array
                }
                searchString = searchString.trim().toLocaleLowerCase();
                article_array = article_array.filter(function (item) {
                    if (item.title.toLowerCase().indexOf(searchString) !== -1) {
                        return item
                    }
                });
                return article_array
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    [v-cloak] {
        display: none;
    }

    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }

    .bar {
        background-color: #42b983;

        box-shadow: 0 1px 1px #ccc;
        border-radius: 2px;
        width: 400px;
        padding: 14px;
        margin: 45px auto 20px;
        position: relative;
    }

    .bar input {
        background: #fff no-repeat 13px 13px;

        border: none;
        width: 100%;
        line-height: 19px;
        padding: 11px 0;

        border-radius: 2px;
        box-shadow: 0 2px 8px #c4c4c4 inset;
        text-align: left;
        font-size: 14px;
        font-family: inherit;
        color: #738289;
        font-weight: bold;
        outline: none;
        text-indent: 40px;
    }

    ul {
        list-style: none;
        width: 428px;
        margin: 0 auto;
        text-align: left;
    }

    ul li {
        border-bottom: 1px solid #ddd;
        padding: 10px;
        overflow: hidden;
    }

    ul li img {
        width: 60px;
        height: 60px;
        float: left;
        border: none;
    }

    ul li p {
        margin-left: 75px;
        font-weight: bold;
        padding-top: 12px;
        color: #6e7a7f;
    }
</style>
