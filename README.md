# potato

let gameOn = false
let shakeCount = 0
let maxShakes = 0
input.onButtonPressed(Button.A, function () {
    gameOn = true
    shakeCount = 0
    // Random shakes before explosion
    maxShakes = randint(5, 15)
    basic.showString("GO")
})
input.onGesture(Gesture.Shake, function () {
    if (gameOn) {
        shakeCount += 1
        basic.showNumber(shakeCount)
        if (shakeCount >= maxShakes) {
            basic.showIcon(IconNames.Skull)
            music.playTone(262, music.beat(BeatFraction.Double))
            gameOn = false
        } else {
            // Passed potato
            basic.showString("P")
        }
    }
})
