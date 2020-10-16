# c# Borderless Window Resize

Simple one-file code to add resizability on a borderless form.

### Usage

```cs
using BorderlessResizer;

this.ApplyWindowResizer();
```

All you need to do is use the namespace and then call `ApplyWindowResizer()` on your Form. That's it!

### Functions

```cs
System.Windows.Forms.Form.ApplyWindowResizer(int grip = 10);
```

Adds resizability to the form. The `grip` variable is used to determine the size of the resizing area, the default is 10.

```cs
GlobalMouseHandler.SuperMouseClick(System.Drawing.Point Location, bool Down)
```

 * System.Drawing.Point `Location`: The location of the click.
 * bool `Down`: True if the left button was pressed, False if it was released.

Event fired if the user left-clicks anywhere, even outside the form.

```cs
GlobalMouseHandler.SuperMouseMove(System.Drawing.Point Location, bool MouseLeft)
```

 * System.Drawing.Point `Location`: The location of the mouse.
 * bool `MouseLeft`: True if the left mouse button is currently being held.

Event fired when the mouse is moved anywhere, even outside the form.

## Alternative

Why write this library when CreateParams exists, providing the same functionality natively? Well, for some reason when I use CreateParams, it adds this annoying bar at the top of the Form that I can't remove. I've also tried `cp.Style |= 0x20000;`, which works exquisitely on the base Form itself, but after I added Panels on top it no longer worked. This is a solution that works, even if you pack 600 panels on top! I hope.

```
protected override CreateParams CreateParams {
    get {
        CreateParams cp = base.CreateParams;
        cp.Style |= 0x40000;
        return cp;
    }
}
```
