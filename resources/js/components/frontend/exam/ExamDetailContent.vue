<template>
    <div class="px-[16px] py-[24px] md:rounded" style="min-height: 100%; min-width: fit-content;">
        <div class="flex unitName mb-4 px-3">
            <div class="rounded p-1.5 bg-[#D3E0FF] text-[#2162FF] w-fit mr-2 font-bold text-sm uppercase flex flex-row">
                <img :src="highlighter" />
                DOING
            </div>
            <div class="text-bold text-xl">
                {{ this.data?.name }}
            </div>
        </div>

        <div class="border-t border-gray-300 w-full h-px"></div>
        <editor
        api-key="9cf2lnudes654k3o56ypikgh86gxhcwsovfrdowhu7awzfwg"
         :init="init()" toolbar="" :disabled="true" :value="content?.description || content?.content" />
    </div>
</template>

<script>
import Editor from "@tinymce/tinymce-vue";
export default {
    components: {
        Editor
    },
    data() {
        return {
            highlighter: require('../../../../../public/images/learn/highlighter.svg'),
            data: null
        }
    },
    methods: {
        init() {
            return {
                plugins: "pagebreak autoresize",
                menubar: "",
                toolbar: "",
                resize: false
            };
        },
    },
    props: ["content"],
    watch: {
        content (newContent) {
            this.data = newContent
        }
    }
}
</script>
<style>
    @media only screen and (max-width: 640px) { 
        .unitName {
            flex-direction: column;
        }
    }
    @media only screen and (min-width: 640px) { 
        .unitName {
            flex-direction: row;
        }
    }
</style>