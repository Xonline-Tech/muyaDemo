<script setup lang="ts">
import {onMounted} from "vue";

import Muya from "@marktext/muya";
import zh from '@marktext/muya/dist/locales/zh';
import MD2Html from '@marktext/muya/dist/state/markdownToHtml';
import {TState} from "@marktext/muya/dist/state/types";

import {
    CodeBlockLanguageSelector,
    EmojiSelector,
    ImageEditTool,
    ImageResizeBar,
    ImageToolBar,
    InlineFormatToolbar,
    ParagraphFrontButton,
    ParagraphFrontMenu,
    ParagraphQuickInsertMenu,
    PreviewToolBar,
    TableColumnToolbar,
    TableDragBar,
    TableRowColumMenu
} from "@marktext/muya/dist/ui";

import '@marktext/muya/dist/assets/style.css'

const props = defineProps({
    id: {
        type: Number,
    }
});

const DEFAULT_MARKDOWN = '111';


Muya.use(EmojiSelector);
Muya.use(InlineFormatToolbar);

Muya.use(ImageToolBar);
Muya.use(ImageResizeBar);
Muya.use(CodeBlockLanguageSelector);

Muya.use(ParagraphFrontButton);
Muya.use(ParagraphFrontMenu);
Muya.use(TableColumnToolbar);
Muya.use(ParagraphQuickInsertMenu);
Muya.use(TableDragBar);
Muya.use(TableRowColumMenu);
Muya.use(PreviewToolBar);

onMounted(() => {

    const element: Element = document.querySelector('#editor' + props.id)!;


    const muya = new Muya(<HTMLElement>element, {});

    muya.locale(zh);

    muya.init()

})
</script>
<template>
    <p style="color: white">{{ props.id }}</p>
    <div :id="'editor'+props.id"></div>
</template>

<style scoped>

</style>