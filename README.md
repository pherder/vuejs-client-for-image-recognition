# Vue.js client application for image recognition

Simple application that consumes response from image recognition webAPI.

## Running

Download repo and run in command line:
```
npm install
npm run serve
```

## Usage

If you want the app to consume response from your API change `apiUri` in `src/views/Recognition.vue` 
```
data() {
    return {
        state: 0,
        apiUri: "http://127.0.0.1:5000/upload/",
        imageUrl: null,
        recognitionResults: null
    };
},
```
and also change line
```
<UploadBox @uploadClicked="exampleUploadImage" v-if="state === 0"/>
```
to
```
<UploadBox @uploadClicked="uploadImage" v-if="state === 0"/>
```
Your server has to make JSON response in format:
```
{
    "Here are some": "1.00",
    "example results": "0.75",
    "from object": "0.50",
    "recognitionResults": "0.00"
}
```

## Built with

* [Vue.js](https://vuejs.org/)

* [Axios](https://github.com/axios/axios)

## License

[MIT License](https://choosealicense.com/licenses/mit/)
