# A demo clock using the requestAnimationFrame &amp; the Date api


*References:*
 
requestAnimationFrame: https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame

date: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleTimeString

optimize: https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution?authuser=1
```js
function Clock(el) {
    if(el === undefined) {
        throw new Error('Missing "el", the DOM element to show date')
    }
    // options for "toLocaleTimeString"
    const timeOptions = {
        hour12: true,
        hour: 'numeric',
        minute: '2-digit',
        second: '2-digit'
    }

    // initial hour
    el.textContent = new Date().toLocaleTimeString(timeOptions)

    let prevTime = 0;

    function run(timestamp){
        // update DOM every second only
        if(timestamp - prevTime > 1000){
            prevTime = timestamp
            const date = new Date()
            el.textContent = date.toLocaleTimeString(timeOptions)
        }
        requestAnimationFrame(run)
    }

    requestAnimationFrame(run)
}
```
