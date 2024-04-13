<!-- 
  structuring the nodes as a directed graph the textbox should have the following properties:
  InNodes (type: Textbox)
  OutNodes (type: Textbox)
  Content (type: Textbox)
  all these can get exported to json obj which can be saved locally (we don't need a database for this scope)
-->

<script>
import { onMount, onDestroy } from 'svelte';
import { Editor } from '@tiptap/core';
import { generateHTML } from '@tiptap/html';
import StarterKit from '@tiptap/starter-kit'
import Typography from '@tiptap/extension-typography';
import Superscript from '@tiptap/extension-superscript';
import Subscript from '@tiptap/extension-subscript';

let element;
let editor;
export let c;
export let text;

onMount(() => {
  editor = new Editor({
    element: element,
    extensions: [
      StarterKit.configure({
        heading: [1,2],
      }),
      Typography,
      Superscript,
      Subscript,
    ],
    editorProps: {
      attributes: {
        class: "prose w-96 min-h-52 transition-all duration-300 bg-gray-50 hover:bg-gray-100 border border-gray-300 text-gray-900 p-2 rounded"
      },
    },
    content: '',
    autofocus: true,
    editable: true,
    onTransaction: () => {
      editor = editor;
    },
    onUpdate: () => {
      text = editor.getHTML();
      console.log(text);
    },
  })
});

onDestroy(() => {
  if (editor) editor.destroy();
});

</script>

<div 
  bind:this={element} 
/>
