/**
  UI built using https://github.com/json-editor/json-editor
 */
<script setup>
import { JSONEditor } from "@json-editor/json-editor/dist/jsoneditor";
import { onMounted, ref } from "vue";
import yaml from "js-yaml";
import DSSSchema from "/src/assets/schema/DSSSchema.json";

const editor = ref({});
const AceEditor = ref({});

onMounted(()=>{

  // Overriding HTML sanitizing for descriptions - since we have control over the Schema
  JSONEditor.AbstractTheme.prototype.getDescription = function(text) {
    const el = document.createElement('p')
    el.innerHTML = text;
    return el
  };
  
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

  // The AceEditor is included from CDN in index.html, it appears clunky to do it via vuejs
  // It's used for 
  // 1) Json highlighting in string fields where format=json. This is set automatically by json-editor
  // 2) YAML highlighting in the data in/out text field. This is configured below
  AceEditor.value = ace.edit("theYAMLData");
  AceEditor.value.session.setMode("ace/mode/yaml");

})

function setEditorValue(event){
  editor.value.setValue(yaml.load(AceEditor.value.getValue()));
}

function setYAMLValue(event){
  AceEditor.value.setValue(yaml.dump(editor.value.getValue()));
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
  <div class="infoBox">
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
    <div class="row" v-show="YAMLField.visible" style="padding: 15px;">
      <div class="col" id="theYAMLData" style="height: 400px;border: 1px solid black; border-radius: 0.25em;"/>
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


