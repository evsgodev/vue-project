<template>
  <div class="container">
    <div class="form-group">
        <input type="text" placeholder value />
    </div>
    <div class="row">
        <div class="col-12">
            <label class="label-inline">
                Colors: 
                <select class="textarea-options" name="colors" id="selectedColors">
                    <option value="#7E9DD3">Chetwode</option>
                    <option value="#8D1116">Tamarillo</option>
                    <option value="#118D3C">Salem</option>
                    <option value="#319052">Sea Green</option>
                    <option value="#87C59C">De York</option>
                    <option value="#5F43CB">Purple Heart</option>
                    <option value="#B71F97">Red Violet</option>
                    <option value="#C6395C">Hibiscus</option>
                    <option value="#C6BF39">Earls Green</option>
                    <option value="#38F0E3">Bright Turquoise</option>
                </select>
            </label>
            <label class="label-inline">
                Font Family: 
                <select class="textarea-options" name="font_family" id="selectedFont">
                    <option value="Arial">Arial</option>
                    <option value="Calibri">Calibri</option>
                    <option value="Consolas">Consolas</option>
                    <option value="Georgia">Georgia</option>
                </select>
            </label>
            <label class="label-inline">
                Font Size: 
                <select class="textarea-options" name="font_size" id="selectedFontSize">
                    <option value="16">16 px</option>
                    <option value="18">18 px</option>
                    <option value="20">20 px</option>
                    <option value="24">24 px</option>
                    <option value="32">32 px</option>
                    <option value="36">36 px</option>
                    <option value="40">40 px</option>
                    <option value="48">48 px</option>
                </select>
            </label>
            <div class="textarea">
                <textarea rows="1" id="dlEditor" data-autoresize data-font-size="16"></textarea>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */

export default {
    name: "InputText",
    props: {
        data: {
            type: Object
        }
    },
    mounted() {
        const getTextAreaHeight = () => {
            document.querySelectorAll('[data-autoresize]').forEach(element => {
                const offset = element.offsetHeight - element.clientHeight;
                const fontSize = Number(element.getAttribute('data-font-size'));

                const calcMaxHeight = () => (element.clientHeight) * 8;
                
                const maxHeight = calcMaxHeight();

                const handlerInputText = event => {
                    if (event.target.clientHeight > maxHeight) {
                        event.target.style.height = maxHeight
                        return;
                    } else {
                        event.target.style.height = 'auto';
                        event.target.style.height = `${event.target.scrollHeight + offset}px`;
                    }
                }

                element.addEventListener('input', event => handlerInputText(event));
                element.addEventListener('paste', event => {
                    handlerInputText(event);
                });
            });
        }

        getTextAreaHeight();

        const labelSelect = document.querySelectorAll('.label-inline select');

        labelSelect.forEach(item => {
            item.addEventListener('change', event => {
                const select = event.target;
                const selectId = select.getAttribute('id');
                const target = document.querySelector('#dlEditor');

                switch (selectId) {
                    case 'selectedColors':
                        target.style.color = select.value;
                        break;
                    case 'selectedFont':
                        target.style.fontFamily = select.value;
                        break;
                    case 'selectedFontSize':
                        let text = null;
                        
                        target.style.fontSize = `${select.value}px`;
                        text = target.value;
                        target.value = '';
                        target.style.height = 'auto';
                        target.setAttribute('data-font-size', select.value);
                        getTextAreaHeight();
                        setTimeout(() => {
                            target.value = text;
                        }, 200);
                        break;
                }
            });
        })
    }
}
</script>

<style scope>
    textarea {
        resize: none;
        max-width: 600px;
        width: 100%;
    }

    .label-inline {
        display: inline-block;
        margin: 0 16px 16px 0;
    }

    .label-inline:last-child {
        margin-right: 0;
    }
</style>