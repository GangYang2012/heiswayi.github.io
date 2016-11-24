---
layout: post
title: XAML - Better Way To Scale Icon In Path
description: A better way to scale an icon built using Path element.
keywords: xaml icon, icon scaling, wpf
---

Creating an icon in XAML gives us a flexibility in our software UI development. The best tool to do that is [Microsoft Expression Design 4](http://www.microsoft.com/en-my/download/details.aspx?id=36180). The ability to export the design into any popular format such as BMP, JPG, PNG, XAML, etc. is a beautiful feature. Assuming we have designed our icon and exported it into XAML in order to get the `StreamGeometry` mini-language. Then, we can use this `StreamGeometry` data for `Data` property in a `Path` element.

![Using ScaleTransform](http://i.imgur.com/jPcRXZL.png)

Let's say the original dimension of the designed icon is 44x44 pixels and we need to scale it bigger to fit our development requirements. INSTEAD of using `ScaleTransform` element from the `Path.RenderTransform` element just to make the icon size bigger, it's BETTER to assign directly the `Width`, `Height` and `Stretch` property in the `Path` element.

### Example

Instead of this:

```xml
<Path Fill="White" Data="F1 M 22.9583,31.6667C 24.27, ..., ..., ... Z ">
    <Path.RenderTransform>
        <ScaleTransform ScaleX="1" ScaleY="1" />
    </Path.RenderTransform>
</Path>
```

Change it to use something like this:

```xml
<Path Width="100" Height="100" Stretch="Uniform" Fill="White" Data="F1 M 22.9583,31.6667C 24.27,31.6667 25.3333,32.73 25.3333,34.0417L 25.3333, ..., ..., ... Z "/>
```

### Conclusion

![Using Path icon scale](http://i.imgur.com/ljsnCT0.png)

> The `Stretch="Uniform"` property makes the `Path` element (the icon) can be scaled up or down with a correct ratio.

This is the sample of mini-language (the `StreamGeometry` data) for the **Android** icon I used:

```
F1 M 22.9583,31.6667C 24.27,31.6667 25.3333,32.73 25.3333,34.0417L 25.3333,43.5417C 25.3333,44.8533 24.27,45.9167 22.9583,45.9167C 21.6467,45.9167 20.5833,44.8533 20.5833,43.5417L 20.5833,34.0417C 20.5833,32.73 21.6467,31.6667 22.9583,31.6667 Z M 53.0416,31.6667C 54.3533,31.6667 55.4166,32.73 55.4166,34.0417L 55.4166,43.5417C 55.4166,44.8533 54.3533,45.9167 53.0416,45.9167C 51.7299,45.9167 50.6666,44.8533 50.6666,43.5417L 50.6666,34.0417C 50.6666,32.73 51.7299,31.6667 53.0416,31.6667 Z M 26.9166,31.6667L 49.0833,31.6667L 49.0833,48.2917C 49.0833,49.6034 48.02,50.6667 46.7083,50.6667L 44.3333,50.6667L 44.3333,55.4167C 44.3333,56.7284 43.27,57.7917 41.9583,57.7917C 40.6466,57.7917 39.5833,56.7284 39.5833,55.4167L 39.5833,50.6667L 36.4166,50.6667L 36.4166,55.4167C 36.4166,56.7284 35.3533,57.7917 34.0416,57.7917C 32.73,57.7917 31.6666,56.7284 31.6666,55.4167L 31.6667,50.6667L 29.2916,50.6667C 27.98,50.6667 26.9166,49.6034 26.9166,48.2917L 26.9166,31.6667 Z M 29.6875,19C 29.9967,18.6909 30.4979,18.6909 30.8071,19L 33.402,21.595C 34.8777,20.9478 36.4641,20.5834 38,20.5834C 39.5494,20.5834 41.1502,20.9543 42.637,21.6122L 45.2491,19C 45.5583,18.6909 46.0596,18.6909 46.3687,19C 46.6779,19.3092 46.6779,19.8105 46.3687,20.1196L 44.1084,22.38C 46.9524,24.1057 49.0833,26.9132 49.0833,30.0834L 26.9166,30.0834C 26.9166,26.9002 29.065,24.0827 31.9266,22.3588L 29.6875,20.1196C 29.3783,19.8105 29.3783,19.3092 29.6875,19 Z M 34.0417,24.5417C 33.1672,24.5417 32.4583,25.2506 32.4583,26.125C 32.4583,26.9995 33.1672,27.7083 34.0417,27.7083C 34.9161,27.7083 35.625,26.9995 35.625,26.125C 35.625,25.2506 34.9161,24.5417 34.0417,24.5417 Z M 41.9583,24.5417C 41.0839,24.5417 40.375,25.2505 40.375,26.125C 40.375,26.9995 41.0839,27.7083 41.9583,27.7083C 42.8328,27.7083 43.5417,26.9995 43.5417,26.125C 43.5417,25.2505 42.8328,24.5417 41.9583,24.5417 Z
```

The reason I'm writing about this because I found out that some people use the `ScaleTransform` element just to resize the icon. This is not the best method when if we intend to keep the icon ratio resized proportionally. Unless we don't care about the scale ratio at all. Since there is a simpler method, why not we apply it as a standard, so we can reduce the probability of human errors. Resizing the icon requires it to keep its scale ratio in order to maintain its shape correctly.
