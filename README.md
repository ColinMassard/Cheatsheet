# Cheatsheet THREE/WebGL errors

## WebGL-00007B58032CA300] GL_INVALID_VALUE: Offset overflows texture dimensions.
```js
// DO not use this. This function is deprecated 
let texture = new THREE.Texture(img)

// Use the following code instead
let image = new Image()
image.src = img.src
let texture = new THREE.Texture(image)
```

## Reveal Animations.
Javascript Module part
```js
export function animation() {
    const element = document.querySelectorAll('[data-animate]');
    if (element === null) return;

    const intersectionObserverScroll = new IntersectionObserver(
        entries => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        },
        {
            rootMargin: '0px',
        },
    );

    element.forEach(animateElement => intersectionObserverScroll.observe(animateElement));
}
```

CSS Part
```css

@mixin transitionDelayPop($default, $step, $firstStep, $lastStep) {
    $currentDuration: $default;

    @for $i from $firstStep through $lastStep {
        &:nth-child(#{$i}) {
            transition-delay: $currentDuration;
        }
        $currentDuration: $currentDuration + $step;
    }
}

.anim-fade-up {
    opacity: 0;
    transform: translate3d(0, 5%, 0);
    transition-property: opacity, transform;
    transition-duration: 0.25s;
    transition-timing-function: 0.25s;
}

.visible {
    &.anim-fade-up,
    .anim-fade-up {
        opacity: 1;
        transform: none;
    }
}

.anim--cascad {
    .anim-fade-up,
    .anim-fade-down,
    .anim-fade {
        @include transitionDelayPop(1000ms, 200ms, 1, 100);
    }
}
.delay {
    transition-delay: 180ms;
}
```

Html Example: 
``` html
<div class="w-container mx-auto anim--cascad"
  id="macy-container"
  data-animate="">
  {% for article in articles %}
  <div class="demo anim-fade-up delay">
    {% endfor %}
  </div>
</div>
```
