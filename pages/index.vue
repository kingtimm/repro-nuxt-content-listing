<template>
    <div>
        <h1>Example 1</h1>
        <p>this uses a query for
        <pre style="display: inline;">queryContent('articles')</pre>
        and only lists the root
        </p>
        <ContentNavigation v-slot="{ navigation }" :query="query">
            <ul>
                <li v-for="link of navigation" :key="link._path">
                    <NuxtLink :to="link._path">{{ link.title }}</NuxtLink>
                </li>
            </ul>
        </ContentNavigation>



        <h1>Example 2</h1>
        <p>this uses the same query
        <pre style="display: inline;">queryContent('articles')</pre>
        but goes on the client side to find the children
        </p>
        <ContentNavigation v-slot="{ navigation }" :query="query">
            <ul>
                <li v-for="link of navigation[0].children" :key="link._path">
                    <NuxtLink :to="link._path">{{ link.title }} - {{ link.publishedAt }}</NuxtLink>
                </li>
            </ul>
        </ContentNavigation>

        <h1>Example 3</h1>
        <p>this uses the same query
        <pre style="display: inline;">queryContent('articles')</pre>
        but goes on the client side to find the children and try to sort them
        </p>
        <ContentNavigation v-slot="{ navigation }" :query="query">
            <ul>
                <li v-for="link of navigation[0].children.reverse()" :key="link._path">
                    <NuxtLink :to="link._path">{{ link.title }} - {{ link.publishedAt }}</NuxtLink>
                </li>
            </ul>
        </ContentNavigation>

        <h1>Example 4</h1>
        <p>this attempts to use the query
        <pre style="display: inline;">queryContent('articles').sort({publishedAt: 1})</pre>
        but I am not sure how to apply query syntax to the child records
        </p>
        <ContentNavigation v-slot="{ navigation }" :query="query">
            <ul>
                <li v-for="link of navigation[0].children" :key="link._path">
                    <NuxtLink :to="link._path">{{ link.title }} - {{ link.publishedAt }}</NuxtLink>
                </li>
            </ul>
        </ContentNavigation>

    </div>
</template>

<script setup lang="ts">
const query = queryContent('articles')
const query4 = queryContent('articles').sort({ publishedAt: 1 }).limit(1)
</script>