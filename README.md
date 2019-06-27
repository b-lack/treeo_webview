# treeo webview

## Getting started
Clone the tensorflow model into the `public` folder.  
```bash
cd public/
git clone https://github.com/Johannes0Horn/treeoTfjsModel.git
```

Install the dependencies.  
```bash
npm install
```

### Config
Rename file `./src/data/config_live_example.js` to `./src/data/config_live.js` and `./src/data/config_stage_example.js` to `./src/data/config_stag.js` and add your server config.

### Build
Buid will create a `www` folder in the [treeo_cordova](https://github.com/b-lack/treeo_cordova) repository.
```bash
npm run build
```

## Ai-Processing
To determine the diameter, an image is processed. This image is taken and processed during data acquisition.  
[./src/components/TreeAddEdit.vue#L380](./src/components/TreeAddEdit.vue#L380)

The image processing happens in two steps.

### Tensorflow
Tensorflow processes the picture. We use the local installed ai-model: [treeoTfjsModels](https://github.com/Johannes0Horn/treeoTfjsModels) in the aiService: [./src/service/aiService.js#L23](./src/service/aiService.js#L23)

The model is loaded in the ai-service:
[./src/service/aiService.js#L16](./src/service/aiService.js#L16)

The model returns a prediction to be processed by opencv [./src/service/aiService.js#L29](./src/service/aiService.js#L29)

### OpenCV
This prediction is processed by the dependency [masksToDiameterService](https://github.com/Johannes0Horn/masksToDiameterService) and returns a diameter. [./src/service/aiService.js#L41](./src/service/aiService.js#L41)

The diameter is added the form [./src/components/TreeAddEdit.vue#L394](./src/components/TreeAddEdit.vue#L394)



## Related Repositories
https://github.com/b-lack/treeo_app  
https://github.com/b-lack/treeo_cordova

## Related Application
https://github.com/fxhinze/treeo_admin  
https://github.com/yalsicor/treeo_api

## License

[Apache License Version 2.0](./LICENSE)
