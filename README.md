# svm.js
svm.js is a Javascript library to render StarView Metafiles to canvas.
Tested in Chrome and Firefox.

## Usage

	<script src="lib/svm.js"></script>

svm.js defines one global function:

	parseSVM(ArrayBuffer | DataView [, Object outArg]) -> HTMLCanvasElement

### To get a canvas

	var canvas = parseSVM(data); // ArrayBuffer or DataView

### To get a Data URL

	var url = parseSVM(data).toDataURL(); // ArrayBuffer or DataView

For more options see [canvas.toDataURL() on MDN](https://developer.mozilla.org/docs/Web/API/HTMLCanvasElement/toDataURL).

### To get a Object URL

	parseSVM(data) // ArrayBuffer or DataView
		.toBlob(function(blob) {
			var url = URL.createObjectURL(blob);
			img.addEventListener('load', function() {
				URL.revokeObjectURL(url);
			});
			img.src = url;
		});
	
This function has less browser support. For more information see
[canvas.toBlob() on MDN](https://developer.mozilla.org/docs/Web/API/HTMLCanvasElement/toBlob).

### To get the number of bytes read

	var out = {};
	var canvas = parseSVM(data, out);
	console.log(out.bytesRead);