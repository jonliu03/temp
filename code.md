function animateValue(id, start, end, duration) {


    var obj = id;
    var range = end - start;
    var minTimer = 50;    
    var stepTime = Math.abs(Math.floor(duration / range));

    stepTime = Math.max(stepTime, minTimer);
    var startTime = new Date().getTime();
    var endTime = startTime + duration;
    var timer;

    function run() {
        var now = new Date().getTime();
        var remaining = Math.max((endTime - now) / duration, 0);
        var value = Math.round(end - (remaining * range));
        obj.text = value + "";
        if (value == end) {
            clearInterval(timer);
        }
    }

    timer = setInterval(run, stepTime);
    run();
}
