https://blog.thoughtram.io/angular/2015/06/29/shadow-dom-strategies-in-angular2.html

ViewEncapsulation.None - No Shadow DOM at all. Therefore, also no style encapsulation.
ViewEncapsulation.Emulated - No Shadow DOM but style encapsulation emulation.
ViewEncapsulation.Native - Native Shadow DOM with all it’s goodness.

Shadow DOM creates DOM inside DOM, combining multiple DOM trees into a single hierarchy. These chunks of isolated DOM act as a “shield” around all these global entities such as CSS and JavaScript logic and are locally scoped to one another.
