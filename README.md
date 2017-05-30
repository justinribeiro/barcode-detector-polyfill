# BarcodeDetector Polyfill
Polyfill for BarcodeDetector, part of [shape detection api](https://wicg.github.io/shape-detection-api/)

## Implementation
This is basically a Promise wrapper around DecoderWorker from the [JOB](https://github.com/EddieLa/JOB) barcode decoding library.

Note that currently this polyfill enables detection and decoding of 1D barcodes only, 2D barcodes (EG QR-code) might be added in the future using an additional library.

## Usage
### In the browser
Install:
```
bower install barcode-detector-polyfill
```

Use:
```
<script src="bower_components/barcode-detector-polyfill/BarcodeDetector.min.js"></script>
<script>
  if (! (BarcodeDetector in window)) {
    window.BarcodeDetector = BarcodeDetector
  }
  var barcodeDetector = new BarcodeDetector();
</script>
...
```

### With webpack
Install:
```
npm install --save barcode-detector-polyfill
```

Use:
```
if (BarcodeDetector in window) {
  ContinueToStartTheApp();
} else {
  import('BarcodeDetector').then(function(BarcodeDetector) {
    window.BarcodeDetector = BarcodeDetector;
    ContinueToStartTheApp();
  }).catch(function(err) {
    console.log('Failed to load BarcodeDetector', err);
  });
}
```

### Examples
See the examples folder, or [live demo](https://giladaya.github.io/barcode-detector-polyfill/)
