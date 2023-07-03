# Cheatsheet THREE/WebGL errors

WebGL-00007B58032CA300] GL_INVALID_VALUE: Offset overflows texture dimensions.
```js
// DO not use this. This function is deprecated 
let texture = new THREE.Texture(img)

// Use the following code instead
let image = new Image()
image.src = img.src
let texture = new THREE.Texture(image)
```
