<template>
  <div>
  <h3 class="title">
  Test Plans:
  </h3>
  <v-data-table
    :headers="headers"
    :items="items"
    hide-actions
    item-key="name"
  >
    <template slot="items" slot-scope="props">
      <tr @click="props.expanded = !props.expanded">
        <td>{{ props.item.name }}</td>
        <td class="text-xs-right">{{ props.item.project_id }}</td>
        <td class="text-xs-right">{{ props.item.status }}</td>
        <td class="text-xs-right">{{ props.item.carbs }}</td>
        <td class="text-xs-right">{{ props.item.protein }}</td>
        <td class="text-xs-right">{{ props.item.sodium }}</td>
        <td class="text-xs-right">{{ props.item.calcium }}</td>
        <td class="text-xs-right">{{ props.item.iron }}</td>
      </tr>
    </template>
    <template slot="expand" slot-scope="props">
      <v-data-table
      :headers="headers"
      :items="props.item.cases"
      hide-actions
      item-key="name"
       style="margin: 15px;"
      >
    <template slot="items" slot-scope="props">
      <tr>
        <td>{{ props.item.name }}</td>
        <td class="text-xs-right">{{ props.item.project_id }}</td>
        <td class="text-xs-right">{{ props.item._id }}</td>
        <td class="text-xs-right">{{ props.item.carbs }}</td>
        <td class="text-xs-right">{{ props.item.protein }}</td>
        <td class="text-xs-right">{{ props.item.sodium }}</td>
        <td class="text-xs-right">{{ props.item.calcium }}</td>
        <td class="text-xs-right">{{ props.item.iron }}</td>
      </tr>
    </template>
      </v-data-table>
    </template>
  </v-data-table>
  </div>
</template>

<script>
  import axios from 'axios'
  import plansdata from '../mock/plans.json'
  export default {
    name: 'Plans',
    data: function() {
      return {
        textSearch: "",
        plans: plansdata,
        headers: [{
            text: 'Dessert (100g serving)',
            align: 'left',
            sortable: false,
            value: 'name'
          },
          {
            text: 'Calories',
            value: 'calories'
          },
          {
            text: 'Fat (g)',
            value: 'fat'
          },
          {
            text: 'Carbs (g)',
            value: 'carbs'
          },
          {
            text: 'Protein (g)',
            value: 'protein'
          },
          {
            text: 'Sodium (mg)',
            value: 'sodium'
          },
          {
            text: 'Calcium (%)',
            value: 'calcium'
          },
          {
            text: 'Iron (%)',
            value: 'iron'
          }
        ],
        items: [
    {
        "_id": "5a0354003487b4282cf8e78d",
        "name": "first test plans",
        "project_id": "5a034b893eacdb5e4c5ad345",
        "status": "active",
        "cases": [
            {
                "_id": "5a0b6bee906e29a260c37cd2",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "Submit lead",
                "code": "# h1 Heading 8-) <h2> h2 Heading by HTML</h2> ## h2 Heading ### h3 Heading ## Horizontal Rules ___ --- *** ## Typographic replacements Enable typographer option to see result. (c) (C) (r) (R) (tm) (TM) (p) (P) +- test.. test... test..... test?..... test!.... !!!!!! ???? ,, -- --- \"○Smartypants○[[○○○○, double quotes\" and 'single quotes' ## Emphasis **This is bold text** __This is bold text__ *This is italic text* _This is italic text_ ~~Strikethrough~~ ## Blockquotes > Blockquotes can also be nested... >> ...by using additional greater-than signs right next to each other... > > > ...or with spaces between arrows. ## Lists Unordered + Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start: * Ac tristique libero volutpat at + Facilisis in pretium nisl aliquet - Nulla volutpat aliquam velit + Very easy! Ordered 1. Lorem ipsum dolor sit amet 2. Consectetur adipiscing elit 3. Integer molestie lorem at massa 1. You can use sequential numbers... 1. ...or keep all the numbers as `1.` Start numbering with offset: 57. foo 1. bar ## Code Inline `code` Indented code // Some comments line 1 of code line 2 of code line 3 of code Block code \"fences\" ``` Sample text here... ``` Syntax highlighting ``` javascript var foo = function (bar) { return bar++; }; console.log(foo(5)); ``` ``` go package main import \"fmt\" func main() { fmt.Println(\"Hello, world!\") } ``` ## Tables | Option | Description | | ------ | ----------- | | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | Right aligned columns | Option | Description | | ------:| -----------:| | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | ## Links [vue-markdown](https://github.com/miaolz123/vue-markdown) [link with title](https://github.com/miaolz123/vue-markdown \"VueMarkdown\") Autoconverted link https://github.com/miaolz123/vue-markdown (enable linkify to see) ## Images ![Minion](dist/img/minion.png) Like links, Images also have a footnote style syntax ![Alt text][id] With a reference later in the document defining the URL location: [id]: dist/img/minion.png \"The Dojocat\" ### Emojies > Classic markup: :wink: :cry: :laughing: :yum: > > Shortcuts (emoticons): :-) :-( 8-) ;) ### Subscript / Superscript - 19^th^ - H~2~O ### \\<ins> ++Inserted text++ ### \\<mark> ==Marked text== ### Footnotes Footnote 1 link[^first]. Footnote 2 link[^second]. Inline footnote^[Text of inline footnote] definition. Duplicated footnote reference[^second]. [^first]: Footnote **can have markup** and multiple paragraphs. [^second]: Footnote text. ### Definition lists Term 1 : Definition 1 with lazy continuation. Term 2 with *inline markup* : Definition 2 { some code, part of Definition 2 } Third paragraph of definition 2. _Compact style:_ Term 1 ~ Definition 1 Term 2 ~ Definition 2a ~ Definition 2b ### Abbreviations This is HTML abbreviation example. It converts \"HTML\", but keep intact partial entries like \"xxxHTMLyyy\" and so on. *[HTML]: Hyper Text Markup Language",
                "testcode": [
                    "> Blockquotes can also be nested...",
                    ">> ...by using additional greater-than signs right next to each other...",
                    "> > > ...or with spaces between arrows.",
                    "> > > ...or with spaces between arrows.",
                    "+ Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start:",
                    "",
                    "- Marker character change forces new list start:",
                    "* Ac tristique libero volutpat at",
                    "+ Facilisis in pretium nisl aliquet",
                    "- Nulla volutpat aliquam velit",
                    "+ Very easy!",
                    "# h1 Heading 8-) <h2> h2 Heading by HTML</h2> ## h2 Heading ### h3 Heading ## Horizontal Rules ___ --- *** ## Typographic replacements Enable typographer option to see result. (c) (C) (r) (R) (tm) (TM) (p) (P) +- test.. test... test..... test?..... test!.... !!!!!! ???? ,, -- --- \"○Smartypants○[[○○○○, double quotes\" and 'single quotes' ## Emphasis **This is bold text** __This is bold text__ *This is italic text* _This is italic text_ ~~Strikethrough~~ ## Blockquotes > Blockquotes can also be nested... >> ...by using additional greater-than signs right next to each other... > > > ...or with spaces between arrows. ## Lists Unordered + Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start: * Ac tristique libero volutpat at + Facilisis in pretium nisl aliquet - Nulla volutpat aliquam velit + Very easy! Ordered 1. Lorem ipsum dolor sit amet 2. Consectetur adipiscing elit 3. Integer molestie lorem at massa 1. You can use sequential numbers... 1. ...or keep all the numbers as `1.` Start numbering with offset: 57. foo 1. bar ## Code Inline `code` Indented code // Some comments line 1 of code line 2 of code line 3 of code Block code \"fences\" ``` Sample text here... ``` Syntax highlighting ``` javascript var foo = function (bar) { return bar++; }; console.log(foo(5)); ``` ``` go package main import \"fmt\" func main() { fmt.Println(\"Hello, world!\") } ``` ## Tables | Option | Description | | ------ | ----------- | | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | Right aligned columns | Option | Description | | ------:| -----------:| | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | ## Links [vue-markdown](https://github.com/miaolz123/vue-markdown) [link with title](https://github.com/miaolz123/vue-markdown \"VueMarkdown\") Autoconverted link https://github.com/miaolz123/vue-markdown (enable linkify to see) ## Images ![Minion](dist/img/minion.png) Like links, Images also have a footnote style syntax ![Alt text][id] With a reference later in the document defining the URL location: [id]: dist/img/minion.png \"The Dojocat\" ### Emojies > Classic markup: :wink: :cry: :laughing: :yum: > > Shortcuts (emoticons): :-) :-( 8-) ;) ### Subscript / Superscript - 19^th^ - H~2~O ### \\<ins> ++Inserted text++ ### \\<mark> ==Marked text== ### Footnotes Footnote 1 link[^first]. Footnote 2 link[^second]. Inline footnote^[Text of inline footnote] definition. Duplicated footnote reference[^second]. [^first]: Footnote **can have markup** and multiple paragraphs. [^second]: Footnote text. ### Definition lists Term 1 : Definition 1 with lazy continuation. Term 2 with *inline markup* : Definition 2 { some code, part of Definition 2 } Third paragraph of definition 2. _Compact style:_ Term 1 ~ Definition 1 Term 2 ~ Definition 2a ~ Definition 2b ### Abbreviations This is HTML abbreviation example. It converts \"HTML\", but keep intact partial entries like \"xxxHTMLyyy\" and so on. *[HTML]: Hyper Text Markup Language"
                ]
            },
            {
                "_id": "5a0ca836906e29a260c37cf3",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead2",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e3260906e291760e7b5ca",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead3",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e326f906e291760e7b5d1",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead4",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e3297906e291760e7b5d6",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead5",
                "code": "i am a ~~tast~~ **test**."
            }
        ]
    },
    {
        "_id": "5a0354033487b4282cf8e78e",
        "name": "second",
        "project_id": "5a034b893eacdb5e4c5ad345",
        "status": "active",
        "cases": [
            {
                "_id": "5a0b6bee906e29a260c37cd2",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "Submit lead",
                "code": "# h1 Heading 8-) <h2> h2 Heading by HTML</h2> ## h2 Heading ### h3 Heading ## Horizontal Rules ___ --- *** ## Typographic replacements Enable typographer option to see result. (c) (C) (r) (R) (tm) (TM) (p) (P) +- test.. test... test..... test?..... test!.... !!!!!! ???? ,, -- --- \"○Smartypants○[[○○○○, double quotes\" and 'single quotes' ## Emphasis **This is bold text** __This is bold text__ *This is italic text* _This is italic text_ ~~Strikethrough~~ ## Blockquotes > Blockquotes can also be nested... >> ...by using additional greater-than signs right next to each other... > > > ...or with spaces between arrows. ## Lists Unordered + Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start: * Ac tristique libero volutpat at + Facilisis in pretium nisl aliquet - Nulla volutpat aliquam velit + Very easy! Ordered 1. Lorem ipsum dolor sit amet 2. Consectetur adipiscing elit 3. Integer molestie lorem at massa 1. You can use sequential numbers... 1. ...or keep all the numbers as `1.` Start numbering with offset: 57. foo 1. bar ## Code Inline `code` Indented code // Some comments line 1 of code line 2 of code line 3 of code Block code \"fences\" ``` Sample text here... ``` Syntax highlighting ``` javascript var foo = function (bar) { return bar++; }; console.log(foo(5)); ``` ``` go package main import \"fmt\" func main() { fmt.Println(\"Hello, world!\") } ``` ## Tables | Option | Description | | ------ | ----------- | | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | Right aligned columns | Option | Description | | ------:| -----------:| | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | ## Links [vue-markdown](https://github.com/miaolz123/vue-markdown) [link with title](https://github.com/miaolz123/vue-markdown \"VueMarkdown\") Autoconverted link https://github.com/miaolz123/vue-markdown (enable linkify to see) ## Images ![Minion](dist/img/minion.png) Like links, Images also have a footnote style syntax ![Alt text][id] With a reference later in the document defining the URL location: [id]: dist/img/minion.png \"The Dojocat\" ### Emojies > Classic markup: :wink: :cry: :laughing: :yum: > > Shortcuts (emoticons): :-) :-( 8-) ;) ### Subscript / Superscript - 19^th^ - H~2~O ### \\<ins> ++Inserted text++ ### \\<mark> ==Marked text== ### Footnotes Footnote 1 link[^first]. Footnote 2 link[^second]. Inline footnote^[Text of inline footnote] definition. Duplicated footnote reference[^second]. [^first]: Footnote **can have markup** and multiple paragraphs. [^second]: Footnote text. ### Definition lists Term 1 : Definition 1 with lazy continuation. Term 2 with *inline markup* : Definition 2 { some code, part of Definition 2 } Third paragraph of definition 2. _Compact style:_ Term 1 ~ Definition 1 Term 2 ~ Definition 2a ~ Definition 2b ### Abbreviations This is HTML abbreviation example. It converts \"HTML\", but keep intact partial entries like \"xxxHTMLyyy\" and so on. *[HTML]: Hyper Text Markup Language",
                "testcode": [
                    "> Blockquotes can also be nested...",
                    ">> ...by using additional greater-than signs right next to each other...",
                    "> > > ...or with spaces between arrows.",
                    "> > > ...or with spaces between arrows.",
                    "+ Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start:",
                    "",
                    "- Marker character change forces new list start:",
                    "* Ac tristique libero volutpat at",
                    "+ Facilisis in pretium nisl aliquet",
                    "- Nulla volutpat aliquam velit",
                    "+ Very easy!",
                    "# h1 Heading 8-) <h2> h2 Heading by HTML</h2> ## h2 Heading ### h3 Heading ## Horizontal Rules ___ --- *** ## Typographic replacements Enable typographer option to see result. (c) (C) (r) (R) (tm) (TM) (p) (P) +- test.. test... test..... test?..... test!.... !!!!!! ???? ,, -- --- \"○Smartypants○[[○○○○, double quotes\" and 'single quotes' ## Emphasis **This is bold text** __This is bold text__ *This is italic text* _This is italic text_ ~~Strikethrough~~ ## Blockquotes > Blockquotes can also be nested... >> ...by using additional greater-than signs right next to each other... > > > ...or with spaces between arrows. ## Lists Unordered + Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start: * Ac tristique libero volutpat at + Facilisis in pretium nisl aliquet - Nulla volutpat aliquam velit + Very easy! Ordered 1. Lorem ipsum dolor sit amet 2. Consectetur adipiscing elit 3. Integer molestie lorem at massa 1. You can use sequential numbers... 1. ...or keep all the numbers as `1.` Start numbering with offset: 57. foo 1. bar ## Code Inline `code` Indented code // Some comments line 1 of code line 2 of code line 3 of code Block code \"fences\" ``` Sample text here... ``` Syntax highlighting ``` javascript var foo = function (bar) { return bar++; }; console.log(foo(5)); ``` ``` go package main import \"fmt\" func main() { fmt.Println(\"Hello, world!\") } ``` ## Tables | Option | Description | | ------ | ----------- | | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | Right aligned columns | Option | Description | | ------:| -----------:| | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | ## Links [vue-markdown](https://github.com/miaolz123/vue-markdown) [link with title](https://github.com/miaolz123/vue-markdown \"VueMarkdown\") Autoconverted link https://github.com/miaolz123/vue-markdown (enable linkify to see) ## Images ![Minion](dist/img/minion.png) Like links, Images also have a footnote style syntax ![Alt text][id] With a reference later in the document defining the URL location: [id]: dist/img/minion.png \"The Dojocat\" ### Emojies > Classic markup: :wink: :cry: :laughing: :yum: > > Shortcuts (emoticons): :-) :-( 8-) ;) ### Subscript / Superscript - 19^th^ - H~2~O ### \\<ins> ++Inserted text++ ### \\<mark> ==Marked text== ### Footnotes Footnote 1 link[^first]. Footnote 2 link[^second]. Inline footnote^[Text of inline footnote] definition. Duplicated footnote reference[^second]. [^first]: Footnote **can have markup** and multiple paragraphs. [^second]: Footnote text. ### Definition lists Term 1 : Definition 1 with lazy continuation. Term 2 with *inline markup* : Definition 2 { some code, part of Definition 2 } Third paragraph of definition 2. _Compact style:_ Term 1 ~ Definition 1 Term 2 ~ Definition 2a ~ Definition 2b ### Abbreviations This is HTML abbreviation example. It converts \"HTML\", but keep intact partial entries like \"xxxHTMLyyy\" and so on. *[HTML]: Hyper Text Markup Language"
                ]
            },
            {
                "_id": "5a0ca836906e29a260c37cf3",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead2",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e3260906e291760e7b5ca",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead3",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e326f906e291760e7b5d1",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead4",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e3297906e291760e7b5d6",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead5",
                "code": "i am a ~~tast~~ **test**."
            }
        ]
    },
    {
        "_id": "5a035fe43487b4282cf8e78f",
        "name": "ddddddd2d",
        "project_id": "5a034b893eacdb5e4c5ad345",
        "status": "active",
        "cases": [
            {
                "_id": "5a0b6bee906e29a260c37cd2",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "Submit lead",
                "code": "# h1 Heading 8-) <h2> h2 Heading by HTML</h2> ## h2 Heading ### h3 Heading ## Horizontal Rules ___ --- *** ## Typographic replacements Enable typographer option to see result. (c) (C) (r) (R) (tm) (TM) (p) (P) +- test.. test... test..... test?..... test!.... !!!!!! ???? ,, -- --- \"○Smartypants○[[○○○○, double quotes\" and 'single quotes' ## Emphasis **This is bold text** __This is bold text__ *This is italic text* _This is italic text_ ~~Strikethrough~~ ## Blockquotes > Blockquotes can also be nested... >> ...by using additional greater-than signs right next to each other... > > > ...or with spaces between arrows. ## Lists Unordered + Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start: * Ac tristique libero volutpat at + Facilisis in pretium nisl aliquet - Nulla volutpat aliquam velit + Very easy! Ordered 1. Lorem ipsum dolor sit amet 2. Consectetur adipiscing elit 3. Integer molestie lorem at massa 1. You can use sequential numbers... 1. ...or keep all the numbers as `1.` Start numbering with offset: 57. foo 1. bar ## Code Inline `code` Indented code // Some comments line 1 of code line 2 of code line 3 of code Block code \"fences\" ``` Sample text here... ``` Syntax highlighting ``` javascript var foo = function (bar) { return bar++; }; console.log(foo(5)); ``` ``` go package main import \"fmt\" func main() { fmt.Println(\"Hello, world!\") } ``` ## Tables | Option | Description | | ------ | ----------- | | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | Right aligned columns | Option | Description | | ------:| -----------:| | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | ## Links [vue-markdown](https://github.com/miaolz123/vue-markdown) [link with title](https://github.com/miaolz123/vue-markdown \"VueMarkdown\") Autoconverted link https://github.com/miaolz123/vue-markdown (enable linkify to see) ## Images ![Minion](dist/img/minion.png) Like links, Images also have a footnote style syntax ![Alt text][id] With a reference later in the document defining the URL location: [id]: dist/img/minion.png \"The Dojocat\" ### Emojies > Classic markup: :wink: :cry: :laughing: :yum: > > Shortcuts (emoticons): :-) :-( 8-) ;) ### Subscript / Superscript - 19^th^ - H~2~O ### \\<ins> ++Inserted text++ ### \\<mark> ==Marked text== ### Footnotes Footnote 1 link[^first]. Footnote 2 link[^second]. Inline footnote^[Text of inline footnote] definition. Duplicated footnote reference[^second]. [^first]: Footnote **can have markup** and multiple paragraphs. [^second]: Footnote text. ### Definition lists Term 1 : Definition 1 with lazy continuation. Term 2 with *inline markup* : Definition 2 { some code, part of Definition 2 } Third paragraph of definition 2. _Compact style:_ Term 1 ~ Definition 1 Term 2 ~ Definition 2a ~ Definition 2b ### Abbreviations This is HTML abbreviation example. It converts \"HTML\", but keep intact partial entries like \"xxxHTMLyyy\" and so on. *[HTML]: Hyper Text Markup Language",
                "testcode": [
                    "> Blockquotes can also be nested...",
                    ">> ...by using additional greater-than signs right next to each other...",
                    "> > > ...or with spaces between arrows.",
                    "> > > ...or with spaces between arrows.",
                    "+ Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start:",
                    "",
                    "- Marker character change forces new list start:",
                    "* Ac tristique libero volutpat at",
                    "+ Facilisis in pretium nisl aliquet",
                    "- Nulla volutpat aliquam velit",
                    "+ Very easy!",
                    "# h1 Heading 8-) <h2> h2 Heading by HTML</h2> ## h2 Heading ### h3 Heading ## Horizontal Rules ___ --- *** ## Typographic replacements Enable typographer option to see result. (c) (C) (r) (R) (tm) (TM) (p) (P) +- test.. test... test..... test?..... test!.... !!!!!! ???? ,, -- --- \"○Smartypants○[[○○○○, double quotes\" and 'single quotes' ## Emphasis **This is bold text** __This is bold text__ *This is italic text* _This is italic text_ ~~Strikethrough~~ ## Blockquotes > Blockquotes can also be nested... >> ...by using additional greater-than signs right next to each other... > > > ...or with spaces between arrows. ## Lists Unordered + Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start: * Ac tristique libero volutpat at + Facilisis in pretium nisl aliquet - Nulla volutpat aliquam velit + Very easy! Ordered 1. Lorem ipsum dolor sit amet 2. Consectetur adipiscing elit 3. Integer molestie lorem at massa 1. You can use sequential numbers... 1. ...or keep all the numbers as `1.` Start numbering with offset: 57. foo 1. bar ## Code Inline `code` Indented code // Some comments line 1 of code line 2 of code line 3 of code Block code \"fences\" ``` Sample text here... ``` Syntax highlighting ``` javascript var foo = function (bar) { return bar++; }; console.log(foo(5)); ``` ``` go package main import \"fmt\" func main() { fmt.Println(\"Hello, world!\") } ``` ## Tables | Option | Description | | ------ | ----------- | | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | Right aligned columns | Option | Description | | ------:| -----------:| | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | ## Links [vue-markdown](https://github.com/miaolz123/vue-markdown) [link with title](https://github.com/miaolz123/vue-markdown \"VueMarkdown\") Autoconverted link https://github.com/miaolz123/vue-markdown (enable linkify to see) ## Images ![Minion](dist/img/minion.png) Like links, Images also have a footnote style syntax ![Alt text][id] With a reference later in the document defining the URL location: [id]: dist/img/minion.png \"The Dojocat\" ### Emojies > Classic markup: :wink: :cry: :laughing: :yum: > > Shortcuts (emoticons): :-) :-( 8-) ;) ### Subscript / Superscript - 19^th^ - H~2~O ### \\<ins> ++Inserted text++ ### \\<mark> ==Marked text== ### Footnotes Footnote 1 link[^first]. Footnote 2 link[^second]. Inline footnote^[Text of inline footnote] definition. Duplicated footnote reference[^second]. [^first]: Footnote **can have markup** and multiple paragraphs. [^second]: Footnote text. ### Definition lists Term 1 : Definition 1 with lazy continuation. Term 2 with *inline markup* : Definition 2 { some code, part of Definition 2 } Third paragraph of definition 2. _Compact style:_ Term 1 ~ Definition 1 Term 2 ~ Definition 2a ~ Definition 2b ### Abbreviations This is HTML abbreviation example. It converts \"HTML\", but keep intact partial entries like \"xxxHTMLyyy\" and so on. *[HTML]: Hyper Text Markup Language"
                ]
            },
            {
                "_id": "5a0ca836906e29a260c37cf3",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead2",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e3260906e291760e7b5ca",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead3",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e326f906e291760e7b5d1",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead4",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e3297906e291760e7b5d6",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead5",
                "code": "i am a ~~tast~~ **test**."
            }
        ]
    },
    {
        "_id": "5a0360193487b4282cf8e790",
        "project_id": "5a034b893eacdb5e4c5ad88",
        "name": "444 4asd",
        "status": "active",
        "cases": [
            {
                "_id": "5a0b6bee906e29a260c37cd2",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "Submit lead",
                "code": "# h1 Heading 8-) <h2> h2 Heading by HTML</h2> ## h2 Heading ### h3 Heading ## Horizontal Rules ___ --- *** ## Typographic replacements Enable typographer option to see result. (c) (C) (r) (R) (tm) (TM) (p) (P) +- test.. test... test..... test?..... test!.... !!!!!! ???? ,, -- --- \"○Smartypants○[[○○○○, double quotes\" and 'single quotes' ## Emphasis **This is bold text** __This is bold text__ *This is italic text* _This is italic text_ ~~Strikethrough~~ ## Blockquotes > Blockquotes can also be nested... >> ...by using additional greater-than signs right next to each other... > > > ...or with spaces between arrows. ## Lists Unordered + Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start: * Ac tristique libero volutpat at + Facilisis in pretium nisl aliquet - Nulla volutpat aliquam velit + Very easy! Ordered 1. Lorem ipsum dolor sit amet 2. Consectetur adipiscing elit 3. Integer molestie lorem at massa 1. You can use sequential numbers... 1. ...or keep all the numbers as `1.` Start numbering with offset: 57. foo 1. bar ## Code Inline `code` Indented code // Some comments line 1 of code line 2 of code line 3 of code Block code \"fences\" ``` Sample text here... ``` Syntax highlighting ``` javascript var foo = function (bar) { return bar++; }; console.log(foo(5)); ``` ``` go package main import \"fmt\" func main() { fmt.Println(\"Hello, world!\") } ``` ## Tables | Option | Description | | ------ | ----------- | | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | Right aligned columns | Option | Description | | ------:| -----------:| | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | ## Links [vue-markdown](https://github.com/miaolz123/vue-markdown) [link with title](https://github.com/miaolz123/vue-markdown \"VueMarkdown\") Autoconverted link https://github.com/miaolz123/vue-markdown (enable linkify to see) ## Images ![Minion](dist/img/minion.png) Like links, Images also have a footnote style syntax ![Alt text][id] With a reference later in the document defining the URL location: [id]: dist/img/minion.png \"The Dojocat\" ### Emojies > Classic markup: :wink: :cry: :laughing: :yum: > > Shortcuts (emoticons): :-) :-( 8-) ;) ### Subscript / Superscript - 19^th^ - H~2~O ### \\<ins> ++Inserted text++ ### \\<mark> ==Marked text== ### Footnotes Footnote 1 link[^first]. Footnote 2 link[^second]. Inline footnote^[Text of inline footnote] definition. Duplicated footnote reference[^second]. [^first]: Footnote **can have markup** and multiple paragraphs. [^second]: Footnote text. ### Definition lists Term 1 : Definition 1 with lazy continuation. Term 2 with *inline markup* : Definition 2 { some code, part of Definition 2 } Third paragraph of definition 2. _Compact style:_ Term 1 ~ Definition 1 Term 2 ~ Definition 2a ~ Definition 2b ### Abbreviations This is HTML abbreviation example. It converts \"HTML\", but keep intact partial entries like \"xxxHTMLyyy\" and so on. *[HTML]: Hyper Text Markup Language",
                "testcode": [
                    "> Blockquotes can also be nested...",
                    ">> ...by using additional greater-than signs right next to each other...",
                    "> > > ...or with spaces between arrows.",
                    "> > > ...or with spaces between arrows.",
                    "+ Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start:",
                    "",
                    "- Marker character change forces new list start:",
                    "* Ac tristique libero volutpat at",
                    "+ Facilisis in pretium nisl aliquet",
                    "- Nulla volutpat aliquam velit",
                    "+ Very easy!",
                    "# h1 Heading 8-) <h2> h2 Heading by HTML</h2> ## h2 Heading ### h3 Heading ## Horizontal Rules ___ --- *** ## Typographic replacements Enable typographer option to see result. (c) (C) (r) (R) (tm) (TM) (p) (P) +- test.. test... test..... test?..... test!.... !!!!!! ???? ,, -- --- \"○Smartypants○[[○○○○, double quotes\" and 'single quotes' ## Emphasis **This is bold text** __This is bold text__ *This is italic text* _This is italic text_ ~~Strikethrough~~ ## Blockquotes > Blockquotes can also be nested... >> ...by using additional greater-than signs right next to each other... > > > ...or with spaces between arrows. ## Lists Unordered + Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start: * Ac tristique libero volutpat at + Facilisis in pretium nisl aliquet - Nulla volutpat aliquam velit + Very easy! Ordered 1. Lorem ipsum dolor sit amet 2. Consectetur adipiscing elit 3. Integer molestie lorem at massa 1. You can use sequential numbers... 1. ...or keep all the numbers as `1.` Start numbering with offset: 57. foo 1. bar ## Code Inline `code` Indented code // Some comments line 1 of code line 2 of code line 3 of code Block code \"fences\" ``` Sample text here... ``` Syntax highlighting ``` javascript var foo = function (bar) { return bar++; }; console.log(foo(5)); ``` ``` go package main import \"fmt\" func main() { fmt.Println(\"Hello, world!\") } ``` ## Tables | Option | Description | | ------ | ----------- | | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | Right aligned columns | Option | Description | | ------:| -----------:| | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | ## Links [vue-markdown](https://github.com/miaolz123/vue-markdown) [link with title](https://github.com/miaolz123/vue-markdown \"VueMarkdown\") Autoconverted link https://github.com/miaolz123/vue-markdown (enable linkify to see) ## Images ![Minion](dist/img/minion.png) Like links, Images also have a footnote style syntax ![Alt text][id] With a reference later in the document defining the URL location: [id]: dist/img/minion.png \"The Dojocat\" ### Emojies > Classic markup: :wink: :cry: :laughing: :yum: > > Shortcuts (emoticons): :-) :-( 8-) ;) ### Subscript / Superscript - 19^th^ - H~2~O ### \\<ins> ++Inserted text++ ### \\<mark> ==Marked text== ### Footnotes Footnote 1 link[^first]. Footnote 2 link[^second]. Inline footnote^[Text of inline footnote] definition. Duplicated footnote reference[^second]. [^first]: Footnote **can have markup** and multiple paragraphs. [^second]: Footnote text. ### Definition lists Term 1 : Definition 1 with lazy continuation. Term 2 with *inline markup* : Definition 2 { some code, part of Definition 2 } Third paragraph of definition 2. _Compact style:_ Term 1 ~ Definition 1 Term 2 ~ Definition 2a ~ Definition 2b ### Abbreviations This is HTML abbreviation example. It converts \"HTML\", but keep intact partial entries like \"xxxHTMLyyy\" and so on. *[HTML]: Hyper Text Markup Language"
                ]
            },
            {
                "_id": "5a0ca836906e29a260c37cf3",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead2",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e3260906e291760e7b5ca",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead3",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e326f906e291760e7b5d1",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead4",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e3297906e291760e7b5d6",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead5",
                "code": "i am a ~~tast~~ **test**."
            }
        ]
    },
    {
        "_id": "5a048d1bc6e5777114ccf9b6",
        "project_id": "5a034b893eacdb5e4c5ad366",
        "name": "555 dsad",
        "status": "active",
        "cases": [
            {
                "_id": "5a0b6bee906e29a260c37cd2",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "Submit lead",
                "code": "# h1 Heading 8-) <h2> h2 Heading by HTML</h2> ## h2 Heading ### h3 Heading ## Horizontal Rules ___ --- *** ## Typographic replacements Enable typographer option to see result. (c) (C) (r) (R) (tm) (TM) (p) (P) +- test.. test... test..... test?..... test!.... !!!!!! ???? ,, -- --- \"○Smartypants○[[○○○○, double quotes\" and 'single quotes' ## Emphasis **This is bold text** __This is bold text__ *This is italic text* _This is italic text_ ~~Strikethrough~~ ## Blockquotes > Blockquotes can also be nested... >> ...by using additional greater-than signs right next to each other... > > > ...or with spaces between arrows. ## Lists Unordered + Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start: * Ac tristique libero volutpat at + Facilisis in pretium nisl aliquet - Nulla volutpat aliquam velit + Very easy! Ordered 1. Lorem ipsum dolor sit amet 2. Consectetur adipiscing elit 3. Integer molestie lorem at massa 1. You can use sequential numbers... 1. ...or keep all the numbers as `1.` Start numbering with offset: 57. foo 1. bar ## Code Inline `code` Indented code // Some comments line 1 of code line 2 of code line 3 of code Block code \"fences\" ``` Sample text here... ``` Syntax highlighting ``` javascript var foo = function (bar) { return bar++; }; console.log(foo(5)); ``` ``` go package main import \"fmt\" func main() { fmt.Println(\"Hello, world!\") } ``` ## Tables | Option | Description | | ------ | ----------- | | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | Right aligned columns | Option | Description | | ------:| -----------:| | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | ## Links [vue-markdown](https://github.com/miaolz123/vue-markdown) [link with title](https://github.com/miaolz123/vue-markdown \"VueMarkdown\") Autoconverted link https://github.com/miaolz123/vue-markdown (enable linkify to see) ## Images ![Minion](dist/img/minion.png) Like links, Images also have a footnote style syntax ![Alt text][id] With a reference later in the document defining the URL location: [id]: dist/img/minion.png \"The Dojocat\" ### Emojies > Classic markup: :wink: :cry: :laughing: :yum: > > Shortcuts (emoticons): :-) :-( 8-) ;) ### Subscript / Superscript - 19^th^ - H~2~O ### \\<ins> ++Inserted text++ ### \\<mark> ==Marked text== ### Footnotes Footnote 1 link[^first]. Footnote 2 link[^second]. Inline footnote^[Text of inline footnote] definition. Duplicated footnote reference[^second]. [^first]: Footnote **can have markup** and multiple paragraphs. [^second]: Footnote text. ### Definition lists Term 1 : Definition 1 with lazy continuation. Term 2 with *inline markup* : Definition 2 { some code, part of Definition 2 } Third paragraph of definition 2. _Compact style:_ Term 1 ~ Definition 1 Term 2 ~ Definition 2a ~ Definition 2b ### Abbreviations This is HTML abbreviation example. It converts \"HTML\", but keep intact partial entries like \"xxxHTMLyyy\" and so on. *[HTML]: Hyper Text Markup Language",
                "testcode": [
                    "> Blockquotes can also be nested...",
                    ">> ...by using additional greater-than signs right next to each other...",
                    "> > > ...or with spaces between arrows.",
                    "> > > ...or with spaces between arrows.",
                    "+ Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start:",
                    "",
                    "- Marker character change forces new list start:",
                    "* Ac tristique libero volutpat at",
                    "+ Facilisis in pretium nisl aliquet",
                    "- Nulla volutpat aliquam velit",
                    "+ Very easy!",
                    "# h1 Heading 8-) <h2> h2 Heading by HTML</h2> ## h2 Heading ### h3 Heading ## Horizontal Rules ___ --- *** ## Typographic replacements Enable typographer option to see result. (c) (C) (r) (R) (tm) (TM) (p) (P) +- test.. test... test..... test?..... test!.... !!!!!! ???? ,, -- --- \"○Smartypants○[[○○○○, double quotes\" and 'single quotes' ## Emphasis **This is bold text** __This is bold text__ *This is italic text* _This is italic text_ ~~Strikethrough~~ ## Blockquotes > Blockquotes can also be nested... >> ...by using additional greater-than signs right next to each other... > > > ...or with spaces between arrows. ## Lists Unordered + Create a list by starting a line with `+`, `-`, or `*` + Sub-lists are made by indenting 2 spaces: - Marker character change forces new list start: * Ac tristique libero volutpat at + Facilisis in pretium nisl aliquet - Nulla volutpat aliquam velit + Very easy! Ordered 1. Lorem ipsum dolor sit amet 2. Consectetur adipiscing elit 3. Integer molestie lorem at massa 1. You can use sequential numbers... 1. ...or keep all the numbers as `1.` Start numbering with offset: 57. foo 1. bar ## Code Inline `code` Indented code // Some comments line 1 of code line 2 of code line 3 of code Block code \"fences\" ``` Sample text here... ``` Syntax highlighting ``` javascript var foo = function (bar) { return bar++; }; console.log(foo(5)); ``` ``` go package main import \"fmt\" func main() { fmt.Println(\"Hello, world!\") } ``` ## Tables | Option | Description | | ------ | ----------- | | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | Right aligned columns | Option | Description | | ------:| -----------:| | data | path to data files to supply the data that will be passed into templates. | | engine | engine to be used for processing templates. Handlebars is the default. | | ext | extension to be used for dest files. | ## Links [vue-markdown](https://github.com/miaolz123/vue-markdown) [link with title](https://github.com/miaolz123/vue-markdown \"VueMarkdown\") Autoconverted link https://github.com/miaolz123/vue-markdown (enable linkify to see) ## Images ![Minion](dist/img/minion.png) Like links, Images also have a footnote style syntax ![Alt text][id] With a reference later in the document defining the URL location: [id]: dist/img/minion.png \"The Dojocat\" ### Emojies > Classic markup: :wink: :cry: :laughing: :yum: > > Shortcuts (emoticons): :-) :-( 8-) ;) ### Subscript / Superscript - 19^th^ - H~2~O ### \\<ins> ++Inserted text++ ### \\<mark> ==Marked text== ### Footnotes Footnote 1 link[^first]. Footnote 2 link[^second]. Inline footnote^[Text of inline footnote] definition. Duplicated footnote reference[^second]. [^first]: Footnote **can have markup** and multiple paragraphs. [^second]: Footnote text. ### Definition lists Term 1 : Definition 1 with lazy continuation. Term 2 with *inline markup* : Definition 2 { some code, part of Definition 2 } Third paragraph of definition 2. _Compact style:_ Term 1 ~ Definition 1 Term 2 ~ Definition 2a ~ Definition 2b ### Abbreviations This is HTML abbreviation example. It converts \"HTML\", but keep intact partial entries like \"xxxHTMLyyy\" and so on. *[HTML]: Hyper Text Markup Language"
                ]
            },
            {
                "_id": "5a0ca836906e29a260c37cf3",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead2",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e3260906e291760e7b5ca",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead3",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e326f906e291760e7b5d1",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead4",
                "code": "i am a ~~tast~~ **test**."
            },
            {
                "_id": "5a0e3297906e291760e7b5d6",
                "project_id": "5a09d27ca2fb074f7097b063",
                "name": "submit lead5",
                "code": "i am a ~~tast~~ **test**."
            }
        ]
    }
]
      }
    },
    created() {
     // this.fetchData()
    },
    watch: {
      '$route': 'fetchData'
    },
    /*computed: {
      plans: function() {
        var textSearch = this.textSearch;
        return this.plans.filter(function(plans) {
          console.log(plans);
          return plans;
        });
      }
    },*/
    methods: {
      fetchData() {
        var that = this
        axios.get('http://localhost:64482/api/applications/' + this.$route.params.id + '/Nodes/')
          .then((resp) => {
            // this.suites = resp.data[1].children;
          })
          .catch((err) => {
            console.log(err)
          })
      }
    }
  }
</script>