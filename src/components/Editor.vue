/**
  UI built using https://github.com/json-editor/json-editor
 */
<script setup>
import { JSONEditor } from "@json-editor/json-editor/dist/jsoneditor";
import { onMounted, ref } from "vue";
import yaml from "js-yaml";
import DSSSchema from "/src/assets/schema/DSSSchema.json";
//import DSSMetadata from "/src/test/SEGES.yaml"

const YAMLData = ref("");
const editor = ref({});

onMounted(()=>{
    
    // Initialize the editor with a JSON schema
      editor.value = new JSONEditor(document.getElementById('editor_holder'),{
        
        schema: DSSSchema,
        ajax: true, // If true, JSON Editor will load external URLs in $ref via ajax.
        theme: "bootstrap4",
        iconlib: "fontawesome5",
        disable_edit_json: true, // If true, remove all Edit JSON buttons from objects.
        disable_properties: true, // If true, remove all Edit Properties buttons from objects.
        remove_button_labels: true // Display only icons in buttons. This works only if iconlib is set.


      });
})

function setEditorValue(event){
  //console.info(YAMLData.value);
  editor.value.setValue(yaml.load(YAMLData.value));
}

function setYAMLValue(event){
  //console.info(YAMLData.value);
  YAMLData.value = yaml.dump(editor.value.getValue());
}

const YAMLField = ref({
  visible:false, label:"Show YAML data"
  });

function toggleYAMLField(event)
{
  YAMLField.value.visible = ! YAMLField.value.visible;
  YAMLField.value.label = (YAMLField.value.visible ? "Hide" : "Show") + " YAML data"
}

</script>
<template>
<div>
  <div style="border: 1px solid black; padding: 15px; background-color: #dddddd;">
    <div class="row">
      <div class="col">
        <h2>Converting data between form and YAML</h2>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <button role="button" class="btn btn-primary" @click="toggleYAMLField">{{YAMLField.label}}</button>
      </div>
    </div>
    <div class="row" v-if="YAMLField.visible">
      <div class="col">
        <textarea class="form-control"  style="width: 100%;height: 400px;" v-model="YAMLData"></textarea>
      </div>
    </div>
    <div class="row"><div class="col">&nbsp;</div></div>
    <div class="row">
      <div class="col-sm-3">
        <button class="btn btn-primary" role="button" @click="setEditorValue">Load from YAML to form</button>
      </div>
      <div class="col-sm-1"></div>
      <div class="col-sm-8">
        <button class="btn btn-primary" role="button" @click="setYAMLValue">Load from form to YAML</button>
      </div>
    </div>
    
  </div>
  <div class="row"><div class="col">&nbsp;</div></div>
  <div class="row">
    <div id="editor_holder"></div>
  </div>
</div>
</template>

<style>
  textarea {
    font-family: 'Courier New', Courier, monospace !important;
  }
</style>
