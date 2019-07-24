---
layout: stack-tool
title: Stack Scroll Tool with multiple layers
toolName: StackScroll
toolType: stack
---


<h2 class="title is-2">How to set up the StackScroll tool:</h2>

{% highlight javascript %}
// Init cornerstone tools
cornerstoneTools.init()

const scheme = 'wadouri'
const baseUrl = 'https://mypacs.com/dicoms/'
const series1 = [
    'image_1.dcm',
    'image_2.dcm'
]

const series2 = [
    'image_1.dcm',
    'image_2.dcm'
]

const imageIdsStack1 = series1.map(seriesImage => `${scheme}:${baseUrl}${seriesImage}`
const imageIdsStack2 = series1.map(seriesImage => `${scheme}:${baseUrl}${seriesImage}`

// Add our tool, and set it's mode
const StackScrollTool = cornerstoneTools.StackScrollTool

//define the stack
const stack1 = {
  currentImageIdIndex: 0,
  imageIdsStack1
}


const stack2 = {
  currentImageIdIndex: 0,
  imageIdsStack2
}


const renderer = new cornerstoneTools.stackRenderers.FusionRenderer();

renderer.findImageFn = (imageIds, targetImageId) => {
    return targetImageId
};

console.log("blablabla");

// load images and set the stack
cornerstone.loadImage(imageIds[0]).then((image) => {
  cornerstone.displayImage(element, image)
  cornerstoneTools.addStackStateManager(element, ['stack'])
  cornerstoneTools.addToolState(element, 'stack', stack1)
  cornerstoneTools.addToolState(element, 'stack', stack2)
  cornerstoneTools.addToolState(element, 'stackRenderer', renderer);
  renderer.render(element);
})

cornerstoneTools.addTool(StackScrollToolTool)
cornerstoneTools.setToolActive('StackScrollTool', { mouseButtonMask: 1 })

{% endhighlight %}
