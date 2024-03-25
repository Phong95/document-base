---
sidebar_position: 2
---
# ✨ Style

Style chung cho toàn bộ ứng dụng

```
src
├── styles.scss
```

## styles.scss

Các style được setup sẵn sử dụng cho toàn bộ dự án.

```scss
// Custom Theming for Angular Material
// For more information: https://material.angular.io/guide/theming
@use '@angular/material' as mat;
@use './app/components/sidebar-v2/sidebar-v2-theme.scss' as sidebar;
@use './app/components/header/header-theme' as header;
@use './app/components/forge-viewer/dual-viewer/forge-dual-viewer-theme' as forge-dual-viewer;
@import "../node_modules/angular-calendar/css/angular-calendar.css";
// Plus imports for other components in your app.
@import './app/theme/light-theme.scss';
@import './app/theme/dark-theme.scss';
@import 'swiper/scss';
@import 'swiper/scss/navigation';
@import 'swiper/scss/pagination';
// Include the common styles for Angular Material. We include this here so that you only
// have to load a single css file for Angular Material in your app.
// Be sure that you only ever include this mixin once!
// TODO(v15): As of v15 mat.legacy-core no longer includes default typography styles.
//  The following line adds:
//    1. Default typography styles for all components
//    2. Styles for typography hierarchy classes (e.g. .mat-headline-1)
//  If you specify typography styles for the components you use elsewhere, you should delete this line.
//  If you don't need the default component typographies but still want the hierarchy styles,
//  you can delete this line and instead use:
//    `@include mat.legacy-typography-hierarchy(mat.define-typography-config());`
//@include mat.all-component-typographies();
// TODO(v15): As of v15 mat.legacy-core no longer includes default typography styles.
//  The following line adds:
//    1. Default typography styles for all components
//    2. Styles for typography hierarchy classes (e.g. .mat-headline-1)
//  If you specify typography styles for the components you use elsewhere, you should delete this line.
//  If you don't need the default component typographies but still want the hierarchy styles,
//  you can delete this line and instead use:
//    `@include mat.legacy-typography-hierarchy(mat.define-typography-config());`
@include mat.all-component-typographies();
@include mat.core();
// Define the palettes for your theme using the Material Design palettes available in palette.scss
// (imported above). For each palette, you can optionally specify a default, lighter, and darker
// hue. Available color palettes: https://material.io/design/color/
// $light-primary: mat.define-palette(mat.$white-palette);
// $light-accent: mat.define-palette(mat.$light-blue-palette);
// // The warn palette is optional (defaults to red).
// $light-warn: mat.define-palette(mat.$red-palette);
// // Define a dark theme
// $dark-primary: mat.define-palette(mat.$blue-gray-palette);
// $dark-accent: mat.define-palette(mat.$amber-palette);
// // The warn palette is optional (defaults to red).
// $dark-warn: mat.define-palette(mat.$red-palette);
// $dark-theme: mat.define-dark-theme((
//     color: (
//         primary: $dark-primary,
//         accent: $dark-accent,
//         warn: $dark-warn,
//     )
// ));
// $dark-theme-color: map-get($dark-theme, color);
// $dark-background-palette: map-get($dark-theme-color, background);
// $dark-foreground-palette: map-get($dark-theme-color, foreground);
// Apply the dark theme by default
@include mat.core-theme($light-theme);
// @include mat.button-theme($dark-theme);
//@include mat.all-component-colors($dark-theme);
//@include sidebar.theme($dark-theme);
// Include theme styles for core and each component used in your app.
// Alternatively, you can import and @include the theme mixins for each component
// that you are using.
.light-theme {
    height: -webkit-fill-available;
}

@include mat.all-component-colors($light-theme);
@include sidebar.theme($light-theme);
@include header.theme($light-theme);
@include forge-dual-viewer.theme($light-theme);
.bg-primary {
    background: mat.get-color-from-palette($light-primary, 'darker');
}
.bg-accent {
    background: mat.get-color-from-palette($light-accent, 'darker');
}
.bg-warn {
    background: mat.get-color-from-palette($light-warn, 'default', 0.3);
}
a {
    color: mat.get-color-from-palette($light-foreground-palette, secondary-text);
}
//#region Handle on hover
.hover-background-color {
    &:hover {
        background-color: mat.get-color-from-palette($light-accent, Main, 0.1) !important;
    }
}

.hover-box-shadow-global {
    &:hover {
        box-shadow: 2px 2px 7px 2px rgb(0 0 0 / 30%) !important;
    }
}

.hover-text-decoration-line-underline {
    &:hover {
        text-decoration-line: underline !important;
    }
}

.hover-cursor-pointer {
    &:hover {
        cursor: pointer !important;
    }
}
//#endregion
//#region Loading
.global-loading {
    color: mat.get-color-from-palette($light-primary, Main-contrast);
}
//#endregion
//#region Drop Shadow
.filter-drop-shadow {
    filter: drop-shadow(1px 0px 2px mat.get-color-from-palette($dark-background-palette, card, 1));
}
//#endregion
//#region Background
.background-with-text {
    //background-color: mat.get-color-from-palette($light-background-palette, card, 0.7);
    //background-color: mat.get-color-from-palette($light-background-palette, selected-button);
    background-color: mat.get-color-from-palette($light-accent, Light) !important;
    color: mat.get-color-from-palette($light-accent, Main-contrast) !important;
}
.background-primary-with-text {
    background-color: mat.get-color-from-palette($light-primary, Light) !important;
    color: mat.get-color-from-palette($light-accent, Main-contrast) !important;
}
.background {
    background-color: mat.get-color-from-palette($light-background-palette, card, 1);
}
.icon-selected-bg-color {
    background-color: mat.get-color-from-palette($light-accent, Light, 0.3) !important;
}
.selected-bg-color {
    background-color: mat.get-color-from-palette($light-background-palette, hover);
}
// .mat-icon {
//     //color: #686e7d;
//     opacity: 0.8 !important;
// }
// button
// {
//     .mat-icon {
//         color: inherit;
//     }
// }
//#endregion
//#region Box shadow
.box-shadow-global {
    box-shadow: 2px 2px 7px 2px rgb(0 0 0 / 30%);
}

.box-shadow-top-000
{
    box-shadow: 0px 1px 3px 3px rgb(0 0 0 / 30%);
}

.box-shadow-bot-000
{
    box-shadow: 0px -2px 3px 3px rgba(0, 0, 0, 0.3) !important;
}
//#endregion
//#region Border
.border-solid-global {
    border: solid 1px mat.get-color-from-palette($light-foreground-palette, divider);
}
.border-dashed-global {
    border: dashed 1px mat.get-color-from-palette($light-foreground-palette, divider);
}

.border-dashed-1px-000 {
    border: dashed 1px #000;
}

.border-left-dashed-global {
    border-left: dashed 1px mat.get-color-from-palette($light-foreground-palette, divider) !important;
}
.border-bottom-dashed-global {
    border-bottom: dashed 1px mat.get-color-from-palette($light-foreground-palette, divider);
}
.border-bottom-solid-global {
    border-bottom: solid 1px mat.get-color-from-palette($light-foreground-palette, divider);
}
.border-top-bottom {
    border-bottom: 0.5px solid #e7e7e7;
}

.border-bottom-solid-global-divider {
    border-bottom: solid 1px mat.get-color-from-palette($light-foreground-palette, divider);
}

.border-bottom-solid-global-text {
    border-bottom: solid 1px mat.get-color-from-palette($light-foreground-palette, text);
}

.border-right-solid-global-text
{
    border-right: solid 1px mat.get-color-from-palette($light-foreground-palette, text);
}

.border-left-solid-global-text
{
    border-left: solid 1px mat.get-color-from-palette($light-foreground-palette, text) !important;
}

// .border-bottom-solid-global
// {
//     border-bottom: solid 1px mat.get-color-from-palette($light-foreground-palette, text);
// }

.border-top-solid-global-text
{
    border-top: solid 1px mat.get-color-from-palette($light-foreground-palette, text);
}

.border-solid-global-text {
    border: solid 1px mat.get-color-from-palette($light-foreground-palette, text);
}

.border-bottom-dashed-global-text {
    border-bottom: dashed 1px mat.get-color-from-palette($light-foreground-palette, text);
}

.border-top-dashed-global {
    border-top: dashed 1px mat.get-color-from-palette($light-foreground-palette, divider);
}
//#endregion

//#region Tabs
.mat-ink-bar //, .mat-tab-nav-bar.mat-primary .mat-ink-bar
{
    //background-color: red !important;
    background-color: mat.get-color-from-palette($light-accent-color, Main) !important;
}

mat-tab-body
{
    .mat-mdc-tab-body-content
    {
        padding: 0.5rem !important;
    }
}
//#endregion
//#region Dialog
.cdk-overlay-container
{
    .mat-mdc-dialog-container {
        background: mat.get-color-from-palette($light-background-palette, card, 1) !important;
    }

    // .mat-mdc-dialog-surface
    // {
    //     padding: 1rem;
    // }
}

//#endregion
//#region Color
.color-primary {
    color: mat.get-color-from-palette($light-primary) !important;
}

.color-accent {
    color: mat.get-color-from-palette($light-accent) !important;
}

.color-warn {
    color: mat.get-color-from-palette($light-warn) !important;
}

.color-white {
    color: #fff !important;
}

.color-red {
    color: rgb(244, 67, 54) !important;
}

.color-green {
    color: rgb(124, 179, 66) !important;
}

.color-blue {
    color: rgb(0, 114, 240) !important;
}

.color-yellow {
    color: rgb(241, 196, 15) !important;
}
//#endregion

html,
body {
    height: 100%;
}

body {
    margin: 0;
    font-family: Roboto, "Helvetica Neue", sans-serif;
}

.spacer {
    flex: 1;
}

//#region Margin
.mr-1rem {
    margin: 1rem;
}

.mr-1rem-0 {
    margin: 1rem 0;
}

.mr-0-5px {
    margin: 0 5px;
}

.mr-top--1rem {
    margin-top: -1rem;
}

.mr-top-1rem {
    margin-top: 1rem !important;
}

.mr-top-2rem {
    margin-top: 2rem;
}

.mr-top-0p5rem {
    margin-top: 0.5rem;
}

.mr-top-5px {
    margin-top: 5px;
}

.mr-bot-1rem {
    margin-bottom: 1rem;
}

.mr-bot-0p5rem {
    margin-bottom: 0.5rem;
}

.mr-left-n1p5rem {
    margin-left: -1.5rem !important;
}

.mr-left-1rem {
    margin-left: 1rem !important;
}

.mr-left-1p5rem {
    margin-left: 1.5rem;
}

.mr-left-2rem {
    margin-left: 2rem;
}

.mr-left-3rem {
    margin-left: 3rem;
}

.mr-left-4rem {
    margin-left: 4rem;
}

.mr-left-0p5rem {
    margin-left: 0.5rem !important;
}

.mr-left-n200px
{
    margin-left: -200px !important;
}

.mr-right-0p5rem {
    margin-right: 0.5rem;
}

.mr-right-1rem {
    margin-right: 1rem !important;
}

.mr-right-2rem {
    margin-right: 2rem !important;
}

//#endregion
//#region Width
.width-7rem
{
    width: 7rem !important;
}

.width-10rem
{
    width: 10rem !important;
}

.width-100pc {
    width: 100%;
}

.width-50pc {
    width: 50% !important;
}

.width-25pc {
    width: 25% !important;
}

.min-width-50vw {
    min-width: 50vw !important;
}

.min-width-70vw {
    min-width: 70vw !important;
}

.max-width-100pc {
    max-width: 100% !important;
}

.max-width-10rem {
    max-width: 10rem !important;
}

.width-fit-content
{
    width: fit-content;
}

.min-width-10rem {
    min-width: 10rem !important;
}

.min-width-5rem {
    min-width: 5rem !important;
}

//#endregion

//#region Height
.height-100pc {
    height: 100%;
}

.height-inherit {
    height: inherit;
}

.height-fit-content {
    height: fit-content !important;
}

.height-1rem {
    height: 1rem;
}

.height-1p5rem {
    height: 1.5rem;
}

.height-2rem {
    height: 2rem;
}

.height-3rem {
    height: 3rem !important;
}

.height-4rem {
    height: 4rem !important;
}

.height-5rem {
    height: 5rem !important;
}

//#endregion

//#region Border
.border-none {
    border: none !important;
}

.border-right-dashed-1px
{
    border-right: dashed 1px rgba(0, 0, 0, 0.6);
}

.border-radius-0p5rem {
    border-radius: 0.5rem;
}

.border-radius-1rem {
    border-radius: 1rem;
}

.border-radius-1p5rem {
    border-radius: 1.5rem;
}

.border-radius-50pc {
    border-radius: 50%;
}

//#endregion

//#region Text
.text-align-center {
    text-align: center;
}

.text-align-left {
    text-align: left;
}

.text-align-right {
    text-align: right;
}

.text-ellipsis {
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow: hidden;
}

.text-line-through {
    text-decoration: line-through;
}

.text-underline {
    text-decoration: underline;
}

.font-style-italic {
    font-style: italic;
}

.text-link {
    cursor: pointer;
    text-decoration: none;
    color: rgba(12, 164, 202, 1);
}

.text-color-red {
    color: #f44336;
}

.text-color-success {
    color: #1dd1a1;
}

.font-size-07rem {
    font-size: 0.7rem !important;
}

.font-size-0p7rem {
    font-size: 0.7rem !important;
}

.font-size-08rem {
    font-size: 0.8rem !important;
}

.font-size-0p8rem {
    font-size: 0.8rem !important;
}

.font-size-09rem {
    font-size: 0.9rem !important;
}

.font-size-0p9rem {
    font-size: 0.9rem !important;
}

.font-size-1rem {
    font-size: 1rem !important;
}

.font-size-1p2rem {
    font-size: 1.2rem !important;
}

.font-size-large {
    font-size: large;
}

.font-size-larger {
    font-size: larger;
}

.font-size-x-large {
    font-size: x-large;
}

.font-size-xx-large {
    font-size: xx-large;
}

.font-size-xxx-large {
    font-size: xxx-large;
}

.text-transform-uppercase {
    text-transform: uppercase;
}

.white-space-break-spaces
{
    white-space: break-spaces !important;
}
//#endregion

//#region Scrollbar
::-webkit-scrollbar {
    width: 5px;
    height: 5px;
}


/* Track */

::-webkit-scrollbar-track {
    background: #f1f1f1;
}


/* Handle */

::-webkit-scrollbar-thumb {
    background: #888;
}


/* Handle on hover */

::-webkit-scrollbar-thumb:hover {
    background: #555;
}

//#endregion

//#region Flex

.display-inline-flex {
    display: inline-flex !important;
}

.gap-0p5rem
{
    gap: 0.5rem !important;
}

.display-flex-center {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
}

.display-flex-column-center {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.display-flex {
    display: flex !important;
}

.display-flex-column {
    display: flex !important;
    flex-direction: column !important;
}

.flex-direction-column {
    flex-direction: column !important;
}

.justify-content-center {
    justify-content: center !important;
}

.justify-content-flex-end {
    justify-content: flex-end;
}

.justify-content-space-evenly {
    justify-content: space-evenly;
}

.justify-content-space-between {
    justify-content: space-between;
}

.justify-content-flex-start {
    justify-content: flex-start;
}

.align-items-center {
    align-items: center;
}

.align-items-flex-end {
    align-items: flex-end;
}

.align-items-flex-start {
    align-items: flex-start;
}

.flex-wrap-wrap {
    flex-wrap: wrap;
}

.flex-spacer {
    flex: 1 1 auto;
}

.flex-1 {
    flex: 1;
}

.flex-grow-1
{
    flex-grow: 1;
}

.flex-grow-2
{
    flex-grow: 2;
}

.flex-grow-3
{
    flex-grow: 3 !important;
}

.flex-grow-4
{
    flex-grow: 4 !important;
}

.align-self-stretch
{
    align-self: stretch;
}

.gap-1rem
{
    gap: 1rem;
}

//#endregion

.mat-toolbar {
    height: 44px !important;
}

.box-sizing-border-box {
    box-sizing: border-box;
}

//#region Button
.buttons {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    height: 3rem;
    button + button {
        margin-left: 0.5rem !important;
    }
}

.button-mff
{
    height: 56px !important;
}

.close-button {
    position: absolute !important;
    right: 0;
    top: 0;
    z-index: 9999;
}

.float-right-bottom-button
{
    position: fixed;
    bottom: 10px;
    right: 10px;
}

.float-left-bottom-button {
    position: fixed;
    bottom: 10px;
    left: 10px;
}

//#endregion

//#region Link
a {
    outline: none !important;
    text-decoration: none !important;
    background-color: transparent;
    &:-webkit-any-link {
        cursor: pointer;
    }
}

//#endregion


//#region Overflow
.overflow-hidden {
    overflow: hidden !important;
}

.overflow-auto {
    overflow: auto !important;
}

.overflow-x-hidden {
    overflow-x: hidden !important;
}

.overflow-y-hidden {
    overflow-y: hidden !important;
}

.overflow-y-auto {
    overflow-y: auto !important;
}

.overflow-wrap-break-word
{
    overflow-wrap: break-word !important;
}
//#endregion

//#region Height
.min-height-100pc
{
    min-height: 100% !important;
}

.min-height-3rem {
    min-height: 3rem;
}

.min-height-2p5rem {
    min-height: 2.5rem;
}

.min-height-2rem {
    min-height: 2rem;
}

.min-height-1rem {
    min-height: 1rem;
}

.min-height-1p5rem {
    min-height: 1.5rem;
}

.min-height-0p5rem {
    min-height: 0.5rem;
}

//#endregion

//#region Line Height
.line-height-normal
{
    line-height: normal !important;
}
//#endregion

//#region Message
.message {
    width: 100%;
    //height: 20px;
    line-height: 1.5rem;
    text-align: center;
    color: #1dd1a1;
    padding: 1rem;
    &.error {
        color: red;
    }
}

//#endregion
//#region Loading
.global-loading {
    z-index: 999999;
    width: 100%;
    height: 100%;
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgba(0, 0, 0, 0.6);
    top: 0;
    left: 0;
    flex-direction: column;
    //display: none;
    .shapes {
        min-width: 60px;
        min-height: 60px;
        background: linear-gradient(currentColor 0 0), linear-gradient(currentColor 0 0), linear-gradient(currentColor 0 0), linear-gradient(currentColor 0 0);
        background-size: 21px 21px;
        background-repeat: no-repeat;
        animation: sh5 0.9s infinite cubic-bezier(0.3, 1, 0, 1);
    }
    @keyframes sh5 {
        0% {
            background-position: 0 0, 100% 0, 100% 100%, 0 100%
        }
        33% {
            background-position: 0 0, 100% 0, 100% 100%, 0 100%;
            width: 60px;
            height: 60px
        }
        66% {
            background-position: 100% 0, 100% 100%, 0 100%, 0 0;
            width: 60px;
            height: 60px
        }
        100% {
            background-position: 100% 0, 100% 100%, 0 100%, 0 0
        }
    }
}

//#endregion
//#region Display
.display-none {
    display: none !important;
}

.display-block {
    display: block !important;
}

.visibility-hidden
{
    visibility: hidden !important;
}
//#endregion


//#region Font
.font-weight-bold {
    font-weight: bold !important;
}

.font-weight-bolder {
    font-weight: bolder !important;
}

.font-weight-500 {
    font-weight: 500 !important;
}

.font-weight-normal {
    font-weight: normal !important;
}

//#endregion
//#region Padding
.padding-0p5rem {
    padding: 0.5rem;
}

.padding-0-0p5rem {
    padding: 0 0.5rem;
}

.padding-0-1rem {
    padding: 0 1rem;
}

.padding-1rem {
    padding: 1rem;
}

.padding-top-1rem {
    padding-top: 1rem !important;
}

.padding-top-0p5rem {
    padding-top: 0.5rem !important;
}

.padding-left-0p5rem {
    padding-left: 0.5rem !important;
}

.padding-left-1rem {
    padding-left: 1rem !important;
}

.padding-left-2rem {
    padding-left: 2rem !important;
}

.padding-bot-1rem {
    padding-bottom: 1rem !important;
}

.padding-right-1rem {
    padding-right: 1rem !important;
}

.padding-right-0p5rem {
    padding-right: 0.5rem !important;
}

//#endregion
//#region Other
* {
    box-sizing: border-box;
}

.as-split-gutter {
    background-color: transparent !important;
}

//#endregion
//#region Layout
.header-content-title {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 40px;
    font-size: x-large;
}

.content-title {
    line-height: 2rem;
    font-size: 1.3rem;
    min-height: 2rem;
    padding-bottom: 0.5rem;
    text-align: center;
}

//#endregion
//#region Cursor
.cursor-default {
    cursor: default !important;
}

.cursor-pointer {
    cursor: pointer !important;
}

.cursor-move {
    cursor: move !important;
}

.pointer-events-visible {
    pointer-events: visible !important;
}

.pointer-events-none {
    pointer-events: none !important;
}

//#endregion
//#region Position
.position-relative {
    position: relative;
}

.position-absolute {
    position: absolute !important;
}

.position-fixed {
    position: fixed !important;
}

//#endregion
//#region Col
.col-eq {
    flex: 1 !important;
}

.col-auto {
    width: auto !important;
}

// .col-eq + .col-eq
// {
//     margin-left: 0.5rem;
// }
.col-16px {
    width: 16px !important;
}

.col-24px {
    width: 24px !important;
}

.col-32px {
    width: 32px !important;
}

.col-40px {
    width: 40px !important;
}

.col-80px {
    width: 80px !important;
}

.col-120px {
    width: 120px !important;
}

.col-160px {
    width: 160px !important;
}

.col-200px {
    width: 200px !important;
}

.col-240px {
    width: 240px !important;
}

.col-50pc {
    width: 50% !important;
}

.col-min-200px
{
    min-width: 200px !important;
    flex: 1 !important;
}

.col-1rem
{
    width: 1rem !important;
}

.col-2rem
{
    width: 2rem !important;
}

.col-3rem
{
    width: 3rem !important;
}

.col-4rem
{
    width: 4rem !important;
}

.col-5rem
{
    width: 5rem !important;
}

.col-6rem
{
    width: 6rem !important;
}

.col-7rem
{
    width: 7rem !important;
}

.col-8rem
{
    width: 8rem !important;
}

.col-9rem
{
    width: 9rem !important;
}

.col-10rem
{
    width: 10rem !important;
}

.col-11rem
{
    width: 11rem !important;
}

.col-12rem
{
    width: 12rem !important;
}

.col-13rem
{
    width: 13rem !important;
}

.col-14rem
{
    width: 14rem !important;
}

.col-15rem
{
    width: 15rem !important;
}

.col-16rem
{
    width: 16rem !important;
}

.col-17rem
{
    width: 17rem !important;
}

.col-18rem
{
    width: 18rem !important;
}

.col-19rem
{
    width: 19rem !important;
}

.col-20rem
{
    width: 20rem !important;
}

.col-min-3rem
{
    min-width: 3rem !important;
    flex: 1 !important;
}

.col-min-4rem
{
    min-width: 4rem !important;
    flex: 1 !important;
}

.col-min-5rem
{
    min-width: 5rem !important;
    flex: 1 !important;
}

.col-min-5p5rem
{
    min-width: 5.5rem !important;
    flex: 1 !important;
}

.col-min-6rem
{
    min-width: 6rem !important;
    flex: 1 !important;
}

.col-min-7rem
{
    min-width: 7rem !important;
    flex: 1 !important;
}

.col-min-8rem
{
    min-width: 8rem !important;
    flex: 1 !important;
}

.col-min-9rem
{
    min-width: 9rem !important;
    flex: 1 !important;
}

.col-min-10rem
{
    min-width: 10rem !important;
    flex: 1 !important;
}

.col-min-11rem
{
    min-width: 11rem !important;
    flex: 1 !important;
}

.col-min-12rem
{
    min-width: 12rem !important;
    flex: 1 !important;
}

.col-min-13rem
{
    min-width: 13rem !important;
    flex: 1 !important;
}


[class*="col-"]+[class*="col-"] {
    margin-left: 0.5rem !important;
}

//#endregion
//#region Mat Paginator
/* TODO(mdc-migration): The following rule targets internal classes of paginator that may no longer apply for the MDC version.*/
/* TODO(mdc-migration): The following rule targets internal classes of paginator that may no longer apply for the MDC version.*/
mat-paginator {
    height: 40px;
    display: flex !important;
    align-items: center;
    justify-content: flex-end;
    border-radius: 20px;
}

//#endregion
//#region Mat Form Field

/* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
/* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
.mat-mdc-form-field .mat-focused .mat-form-field-label {
    color: mat.get-color-from-palette($light-accent, Main-contrast) !important;
}

.disable-mff-bottom {
    .mat-mdc-form-field-subscript-wrapper
    {
        display: none !important;
    }
}

.mat-mdc-form-field {
    line-height: 1.5 !important;
}

.border-radius-mat-form-field {
    /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
    /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
    /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
    /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
    /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
    /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
    /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
    /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
    /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
    /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
    .mat-form-field-wrapper {
        padding-bottom: 0px !important;
        margin: 0px !important;
        /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
        /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
        /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
        /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
        /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
        /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
        /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
        /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
        .mat-form-field-flex {
            display: flex !important;
            align-items: center !important;
            margin-top: 0px !important;
            padding: 0 8px 0 8px !important;
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            .mat-form-field-infix {
                padding: 10px 0px !important;
                border-top: unset !important;
                .mat-mdc-select {
                    /* TODO(mdc-migration): The following rule targets internal classes of select that may no longer apply for the MDC version.*/
                    /* TODO(mdc-migration): The following rule targets internal classes of select that may no longer apply for the MDC version.*/
                    /* TODO(mdc-migration): The following rule targets internal classes of select that may no longer apply for the MDC version.*/
                    /* TODO(mdc-migration): The following rule targets internal classes of select that may no longer apply for the MDC version.*/
                    .mat-select-trigger {
                        /* TODO(mdc-migration): The following rule targets internal classes of select that may no longer apply for the MDC version.*/
                        /* TODO(mdc-migration): The following rule targets internal classes of select that may no longer apply for the MDC version.*/
                        .mat-select-arrow-wrapper {
                            transform: unset !important;
                        }
                    }
                }
            }
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            .mat-form-field-prefix {
                top: 0px !important;
            }
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            .mat-form-field-suffix {
                top: 0px !important;
            }
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
            .mat-form-field-outline {
                top: 0 !important;
                /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
                /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
                .mat-form-field-outline-start {
                    border-radius: 20px 0 0 20px !important;
                    min-width: 20px !important;
                }
                /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
                /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
                .mat-form-field-outline-end {
                    border-radius: 0 20px 20px 0 !important;
                }
                /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
                /* TODO(mdc-migration): The following rule targets internal classes of form-field that may no longer apply for the MDC version.*/
                .mat-form-field-outline-gap {
                    border-top-color: unset !important;
                }
            }
        }
    }
}

//#endregion

//#region Color
.green {
    color: #1dd1a1
}

.opacity-0p6 {
    opacity: 0.6;
}
//#endregion

//#region Icon
.icon-20px {
    font-size: 20px;
    height: 20px !important;
    width: 20px !important;
}
//#endregion

//#region Z-Index
.z-index-5
{
    z-index: 5;
}

.z-index-10
{
    z-index: 10;
}
//#endregion

//#region Right Menu

.right-menu
{
    display: inline-flex;
    flex-direction: column;
    min-width: 180px;
    max-width: 280px;
    background-color: rgb(255, 255, 255);
    padding: 6px 0;
    box-shadow: 2px 2px 7px 2px rgb(0 0 0 / 30%);
    border-radius: 0.5rem;
}

.right-menu-item
{
    background-color: transparent;
    cursor: pointer;
    border: none;

    user-select: none;
    min-width: 64px;
    line-height: 36px;
    padding: 0 16px;

    display: flex;
    align-items: center;
    flex-direction: row;
    flex: 1;
    font-weight: bold;
}

.right-menu-item:hover {
    background-color: rgb(208, 208, 208);
}

.right-menu-item:active {
    background-color: rgb(170, 170, 170);
}
//#endregion

```
