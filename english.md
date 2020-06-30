---
title: English Only Resume
layout: home
stylesheet: /resume/resources/main.css
---

<!-- <iframe src="a3.pdf#toolbar=0&navpanes=0"></iframe> -->
<script src="//mozilla.github.io/pdf.js/build/pdf.js"></script>

<!--
<object data="a3.pdf#toolbar=0&navpanes=0" type="application/pdf" style="background-color: #FFFFFF">
  <a href="a3.pdf">Download PDF</a>
</object> -->

<script>

// If absolute URL from the remote server is provided, configure the CORS
// header on that server.
var url = 'english.pdf';

// Loaded via <script> tag, create shortcut to access PDF.js exports.
var pdfjsLib = window['pdfjs-dist/build/pdf'];

// The workerSrc property shall be specified.
pdfjsLib.GlobalWorkerOptions.workerSrc = '//mozilla.github.io/pdf.js/build/pdf.worker.js';

// Asynchronous download of PDF
var loadingTask = pdfjsLib.getDocument(url);
loadingTask.promise.then(function(pdf) {
  console.log('PDF loaded');

  // Fetch the first page
  var pageNumber = 1;
  pdf.getPage(pageNumber).then(function(page) {
    console.log('Page loaded');

    var scale = 4;
    var viewport = page.getViewport({scale: scale});

    // Prepare canvas using PDF page dimensions
    var canvas = document.getElementById('resume1');
    var context = canvas.getContext('2d');
    canvas.height = viewport.height;
    canvas.width = viewport.width;

    // Render PDF page into canvas context
    var renderContext = {
      canvasContext: context,
      viewport: viewport
    };
    var renderTask = page.render(renderContext);
    renderTask.promise.then(function () {
      console.log('Page rendered');
    });
  });


  var pageNumber = 2;
  pdf.getPage(pageNumber).then(function(page) {
    console.log('Page loaded');

    var scale = 4;
    var viewport = page.getViewport({scale: scale});

    // Prepare canvas using PDF page dimensions
    var canvas = document.getElementById('resume2');
    var context = canvas.getContext('2d');
    canvas.height = viewport.height;
    canvas.width = viewport.width;

    // Render PDF page into canvas context
    var renderContext = {
      canvasContext: context,
      viewport: viewport
    };
    var renderTask = page.render(renderContext);
    renderTask.promise.then(function () {
      console.log('Page rendered');
    });
  });



}, function (reason) {
  // PDF loading error
  console.error(reason);
});
</script>


<div id="resume_container">
    <canvas id="resume1"></canvas>
    <canvas id="resume2"></canvas>
</div>  
