<template>
    <div>
        <aside class="sidebar" :style="{
            marginTop: showV2Tips ? '2.3rem' : 0,
        }">
            <a target="_blank" class="jump-linker" href="https://cool-js.com/temp/server.html">
                <img src="https://cdn.uviewui.com/uview/resources/15645618545.png" />
            </a>
            <a target="_blank" class="jump-linker" href="https://www.jnpfsoft.com/index.html?from=uview">
                <img src="https://cdn.uviewui.com/uview/resources/4565165154.jpg" />
            </a>
            <a target="_blank" class="jump-linker" href="https://code.fun/">
                <img src="https://cdn.uviewui.com/uview/resources/codeFun.jpg" />
            </a>
            <NavLinks />
            <slot name="top" />
            <SidebarLinks :depth="0" :items="items" />
            <slot name="bottom" />
        </aside>
    </div>
</template>

<script>
import SidebarLinks from "@theme/components/SidebarLinks.vue";
import NavLinks from "@theme/components/NavLinks.vue";

export default {
    name: "Sidebar",

    components: {
        SidebarLinks,
        NavLinks,
    },
    data() {
        return {
            // showV2Tips: !localStorage.getItem("showV2Tips"),
        };
    },
    props: ["items"],
    created() { },
    methods: {},
};
</script>

<style lang="stylus">
.sidebar {
    .jump-linker {
        margin-top: 1rem;
        margin-right: 2rem;
        border-radius: 4px;
        width: 170px;
        height: 80px;

        img {
            max-width: 100%;
            border-radius: 4px;
        }
    }

    ul {
        padding: 0;
        margin: 0;
        list-style-type: none;
    }

    a {
        display: inline-block;
    }

    .nav-links {
        display: none;
        border-bottom: 1px solid $borderColor;
        padding: 0.5rem 0 0.75rem 0;

        a {
            font-weight: 600;
        }

        .nav-item, .repo-link {
            display: block;
            line-height: 1.25rem;
            font-size: 1.1em;
            padding: 0.5rem 0 0.5rem 1.5rem;
        }
    }

    &>.sidebar-links {
        padding: 1.5rem 0;
        padding-top: 1rem;

        &>li>a.sidebar-link {
            font-size: 1.1em;
            line-height: 1.7;
            font-weight: bold;
        }

        &>li:not(:first-child) {
            margin-top: 0.75rem;
        }
    }
}

@media (max-width: $MQMobile) {
    .sidebar {
        .nav-links {
            display: block;

            .dropdown-wrapper .nav-dropdown .dropdown-item a.router-link-active::after {
                top: calc(1rem - 2px);
            }
        }

        &>.sidebar-links {
            padding: 1rem 0;
        }
    }
}
</style>
