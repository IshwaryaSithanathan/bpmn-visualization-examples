# Switch tab (of the page) on click on a call activity

Javascript example to demonstrate how to open a new BPMN diagram in a tab.
- [__:fast_forward: live environment__](https://cdn.statically.io/gh/process-analytics/bpmn-visualization-examples/master/examples/interaction/call-activity-with-tabs-on-click/index.html)
- to run locally, open the [index.html](index.html) directly in a Web Browser

## ♻️ Usage

After the main `BpmnVisualization` instantiation, get the HTML element corresponding to the call activity to add a listener and activate the tab (and deactivate the others).

⚠️  In order to avoid having to many content in the README, we simplify it. You can find all the content of the example in [index.js](index.js).
```javascript
const callActivityElt = mainBpmnVisualization.htmlElementRegistry.getBpmnHtmlElement('call_activity');
callActivityElt.onclick = () => {
    openTab('secondary');

    secondaryBpmnVisualization.load(getCalledBpmnDiagram(), { fit: {type: 'Center'} });
}
```

⚠️ The secondary `BPMN container` (in charge of displaying the Call Activity) must be visible during the BPMN diagram loading, otherwise, some BPMN elements won't be displayed.

⚠️ It's not possible to manipulate the class of the HTML element with the zoom, the panning and the fit features, because it recalculated and is overidden by them. \
A new API comes later to support this case.