# -Bootstrap-
总结资料：


概观
用于布置Bootstrap项目的组件和选项，包括包装容器，强大的网格系统，灵活的媒体对象和响应式实用程序类。

集装箱
容器是Bootstrap中最基本的布局元素，在使用我们的默认网格系统时是必需的。选择一个响应式的固定宽度的容器（意味着它max-width在每个断点处的变化）或流体宽度（意味着它100%始终是宽的）。

虽然容器可以嵌套，但大多数布局不需要嵌套容器。


<div class="container">
  <!-- Content here -->
</div>
使用.container-fluid了全宽的容器，跨越视口的整个宽度。


<div class="container-fluid">
  ...
</div>
响应的断点
由于Bootstrap首先是移动开发的，我们使用一些媒体查询为我们的布局和界面创建合理的断点。这些断点主要基于最小的视口宽度，并允许我们随着视口更改而放大元素。

Bootstrap主要在我们的源代码Sass文件中使用以下媒体查询范围（或断点）来进行布局，网格系统和组件。


// Extra small devices (portrait phones, less than 576px)
// No media query since this is the default in Bootstrap

// Small devices (landscape phones, 576px and up)
@media (min-width: 576px) { ... }

// Medium devices (tablets, 768px and up)
@media (min-width: 768px) { ... }

// Large devices (desktops, 992px and up)
@media (min-width: 992px) { ... }

// Extra large devices (large desktops, 1200px and up)
@media (min-width: 1200px) { ... }
由于我们在Sass中编写源代码CSS，所以我们所有的媒体查询都可以通过Sass mixins：


@include media-breakpoint-up(xs) { ... }
@include media-breakpoint-up(sm) { ... }
@include media-breakpoint-up(md) { ... }
@include media-breakpoint-up(lg) { ... }
@include media-breakpoint-up(xl) { ... }

// Example usage:
@include media-breakpoint-up(sm) {
  .some-class {
    display: block;
  }
}
我们偶尔会使用其他方向的媒体查询（给定的屏幕尺寸或更小）：

// Extra small devices (portrait phones, less than 576px)
@media (max-width: 575px) { ... }

// Small devices (landscape phones, less than 768px)
@media (max-width: 767px) { ... }

// Medium devices (tablets, less than 992px)
@media (max-width: 991px) { ... }

// Large devices (desktops, less than 1200px)
@media (max-width: 1199px) { ... }

// Extra large devices (large desktops)
// No media query since the extra-large breakpoint has no upper bound on its width
再次，这些媒体查询也可以通过Sass mixins：


@include media-breakpoint-down(xs) { ... }
@include media-breakpoint-down(sm) { ... }
@include media-breakpoint-down(md) { ... }
@include media-breakpoint-down(lg) { ... }
还有媒体查询和混合使用最小和最大断点宽度来定位单个屏幕大小段。


// Extra small devices (portrait phones, less than 576px)
@media (max-width: 575px) { ... }

// Small devices (landscape phones, 576px and up)
@media (min-width: 576px) and (max-width: 767px) { ... }

// Medium devices (tablets, 768px and up)
@media (min-width: 768px) and (max-width: 991px) { ... }

// Large devices (desktops, 992px and up)
@media (min-width: 992px) and (max-width: 1199px) { ... }

// Extra large devices (large desktops, 1200px and up)
@media (min-width: 1200px) { ... }
这些媒体查询也可以通过Sass mixins：


@include media-breakpoint-only(xs) { ... }
@include media-breakpoint-only(sm) { ... }
@include media-breakpoint-only(md) { ... }
@include media-breakpoint-only(lg) { ... }
@include media-breakpoint-only(xl) { ... }
同样，媒体查询可能会跨越多个断点宽度：


// Example
// Apply styles starting from medium devices and up to extra large devices
@media (min-width: 768px) and (max-width: 1199px) { ... }
Sass mixin针对相同的屏幕尺寸范围将是：


@include media-breakpoint-between(md, xl) { ... }
Z-指数
几个Bootstrap组件使用z-indexCSS属性，通过提供第三个轴来安排内容来帮助控制布局。我们在Bootstrap中使用了一个默认的z-索引尺度，这个尺度被设计为正确的分层导航，工具提示和弹出窗口，模态等等。

我们不鼓励定制这些价值观; 如果你改变一个，你可能需要改变它们。



$zindex-dropdown:          1000 !default;
$zindex-sticky:            1020 !default;
$zindex-fixed:             1030 !default;
$zindex-modal-backdrop:    1040 !default;
$zindex-modal:             1050 !default;
$zindex-popover:           1060 !default;
$zindex-tooltip:           1070 !default;
背景元素（如允许点击消除的背景）倾向于位于较低z-index的位置，而导航和弹出使用较高z-index的位置以确保覆盖周围的内容。

此外，所述button-group，input-group，list-group，和pagination部件利用设定z-index到1或2以确保边界有源元件正确显示的“上方”的兄弟元素。


















