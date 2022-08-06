
# Turbo Laravel Helpers

The missing stimulus helpers for laravel blade! This package contains a bunch of helpers that pairs nicely with `tonysm/turbo-laravel` package. 
Inspired by Symfony UX Stimulus.


## Installation

```bash
  composer require flixtechs-labs/turbo-laravel-helpers
```
    
## Usage
The are 3 main helpers 

- `stimulus_controller()` to add a controller
- `stimulus_action()` to specifiy the action
- `stimulus_target()` to specifiy the target


```blade
<div {{ stimulus_controller('say-hello') }}>
    <input type="text" {{ stimulus_target('say-hello', 'name') }}>

    <button {{ stimulus_action('say-hello', 'greet') }}>
        Greet
    </button>

    <div {{ stimulus_target('say-hello', 'output') }}></div>
</div>
```
The `stimulus_controller('say-hello')` renders a `data-controller="say-hello"` attribute. 
Whenever this element appears on the page, Stimulus will automatically look for and initialize a controller called `say-hello-controller.js`. 
Create that in your `resources/js/controllers/` directory:

```javascript
// resources/js/controllers/say_hello_controller.js
import { Controller } from '@hotwired/stimulus';

export default class extends Controller {
    static targets = ['name', 'output']

    greet() {
      this.outputTarget.textContent = `Hello, ${this.nameTarget.value}!`
    }
}
```




## Testing
```bash
composer test
```
## License

[MIT](https://choosealicense.com/licenses/mit/)

