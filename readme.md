<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Football Formation</title>
    <link rel="stylesheet" href="/index.css">
</head>
<body>
    <div>
        <input type ="radio" name="formation" class="visually-hidden" id="f433" checked>
        <input type ="radio" name="formation" class="visually-hidden" id="f442" checked>
        <input type ="radio" name="formation" class="visually-hidden" id="f352" checked>
        <input type ="radio" name="formation" class="visually-hidden" id="f4321" checked>
        <input type ="radio" name="formation" class="visually-hidden" id="f532" checked>

    </div>

    <h1>Team Formation</h1>

    <div class="controls">
        <label for="f433">4-3-3</label>
        <label for="f442">4-4-2</label>
        <label for="f352">3-5-2</label>
        <label for="f4321">4-3-2-1</label>
        <label for="f532">5-3-2</label>
    </div>

    <div class="pitch">

        <!--anchored positions-->

        <div class="position gk"></div>

        <div class="position lb"></div>
        <div class="position lcb"></div>
        <div class="position rcb"></div>
        <div class="position rb"></div>

        <div class="position lm"></div>
        <div class="position cm"></div>
        <div class="position rm"></div>

        <div class="position lw"></div>
        <div class="position st"></div>
        <div class="position rw"></div>


        <!--players-->

        <div class="player p1"><svg><use href="#player-icon"></use></svg></div>
        <div class="player p2"><svg><use href="#player-icon"></use></svg></div>
        <div class="player p3"><svg><use href="#player-icon"></use></svg></div>
        <div class="player p4"><svg><use href="#player-icon"></use></svg></div>
        <div class="player p5"><svg><use href="#player-icon"></use></svg></div>
        <div class="player p6"><svg><use href="#player-icon"></use></svg></div>
        <div class="player p7"><svg><use href="#player-icon"></use></svg></div>
        <div class="player p8"><svg><use href="#player-icon"></use></svg></div>
        <div class="player p9"><svg><use href="#player-icon"></use></svg></div>
        <div class="player p10"><svg><use href="#player-icon"></use></svg></div>
        <div class="player p11"><svg><use href="#player-icon"></use></svg></div>

        </div>
    </div>

     <svg width="0" height="0" style="position:absolute">
            <symbol id="player-icon" viewBox="0 0 16 16">
                <path d="M8 7C9.65685 7 11 5.65685 11 4c11 2.34315 9.65685 1" fill="currentColor"></path>
            </symbol>
        </svg>

        <!--

<svg width="0" height="0" style="position:absolute">
	<symbol id="player-icon" viewBox="0 0 24 24">
		<path opacity="0.15" d="M3 7L6 4H9C9 4.39397 9.0776 4.78407 9.22836 5.14805C9.37913 5.51203 9.6001 5.84274 9.87868 6.12132C10.1573 6.3999 10.488 6.62087 10.8519 6.77164C11.2159 6.9224 11.606 7 12 7C12.394 7 12.7841 6.9224 13.1481 6.77164C13.512 6.62087 13.8427 6.3999 14.1213 6.12132C14.3999 5.84274 14.6209 5.51203 14.7716 5.14805C14.9224 4.78407 15 4.39397 15 4H18L21 7L20.5 12L18 10.5V20H6V10.5L3.5 12L3 7Z" fill="currentColor"></path>
	<path d="M3 7L6 4H9C9 4.39397 9.0776 4.78407 9.22836 5.14805C9.37913 5.51203 9.6001 5.84274 9.87868 6.12132C10.1573 6.3999 10.488 6.62087 10.8519 6.77164C11.2159 6.9224 11.606 7 12 7C12.394 7 12.7841 6.9224 13.1481 6.77164C13.512 6.62087 13.8427 6.3999 14.1213 6.12132C14.3999 5.84274 14.6209 5.51203 14.7716 5.14805C14.9224 4.78407 15 4.39397 15 4H18L21 7L20.5 12L18 10.5V20H6V10.5L3.5 12L3 7Z" stroke="#000000" stroke-width="1" stroke-linecap="square" stroke-linejoin="round" fill="currentColor"></path>
	</symbol>
</svg>
-->

</body>
</html>

@import url(https://fonts.bunny.net/css?family=jura:300,500);
@layer base, controls, demo;

@layer demo {
:root {
--player-transition-duration: 500ms;
--player-transition-easing: ease-in-out;
--player-color: white;
--player-color-gk: #333; /_goalkeeper_/
--player-size: min(5vw, 50px);
}

    .wrapper {
        display: grid;
        gap: 1rem;
    }

    h1 {
        text-align: center;
        font-size: 1rem;
    }

    .pitch {
        display: grid;
        grid-template-columns: repeat(8, 1fr);
        grid-template-rows: repeat(9, 1fr);
        width: min(90vw, 800px);
        aspect-ratio: 3 / 2;
        position: relative;
        background:
            /*linear-gradient(90deg, #fff 1px, #0000 0) 50% no-repeat,*/
            /*linear-gradient(180deg, #fff 1px, #0000 0) 50% no-repeat,*/
            radial-gradient(1Q, #0000 5w, #ffff 0 calc(5w + 1px), #0000 0),
            repeating-linear-gradient(90deg, #3fae5a 0 5vw, #38a352 0 10vw);
        border: 1px solid white;

        &::after {
            content: '';
            position: absolute;
            left: 50%;
            width: 1px;
            height: 100%;
            background: white;
        }
    }

    /*anchor positions - theese are what changed according to the formation*/

    .position {
        &.gk {
            anchor-name: --gk;
        }
        &.lb {
            anchor-name: --lb;
        }
        &.lcb {
            anchor-name: --lcb;
        }
        &.rcb {
            anchor-name: --rcb;
        }
        &.rb {
            anchor-name: --rb;
        }
        &.lm {
            anchor-name: --lm;
        }
        &.cm {
            anchor-name: --cm;
        }
        &.rm {
            anchor-name: --rm;
        }
        &.lw {
            anchor-name: --lw;
        }
        &.st {
            anchor-name: --st;
        }
        &.rw {
            anchor-name: --rw;
        }
    }

    /*players - follow anchors*/
    .player {
        position: absolute;
        inset: anchor(center);
        translate: -50% -50%;
        display: grid;
        place-content: center;
        color: var(--player-color);
        transition: inset var(--player-transition-duration)
            var(--player-transition-easing);
        /*outline: 1px dashed red;*/
        width: var(--player-size);
        aspect-ratio: 1;
        svg {
            width: 100%;
            height: 100%;
        }
        /*bind players to anchors - these don't change but will
        transition as their anchors are repositioned*/

        &.p1 {
            position-anchor: --gk;
            color: var(--player-color-gk);
        } /* goalkeeper */
        &.p2 {
            position-anchor: --lb;
        }
        &.p3 {
            position-anchor: --lcb;
        }
        &.p4 {
            position-anchor: --rcb;
        }
        &.p5 {
            position-anchor: --rb;
        }
        &.p6 {
            position-anchor: --lm;
        }
        &.p7 {
            position-anchor: --cm;
        }
        &.p8 {
            position-anchor: --rm;
        }
        &.p9 {
            position-anchor: --lw;
        }
        &.p10 {
            position-anchor: --st;
        }
        &.p11 {
            position-anchor: --rw;
        }
    }

    /*Define ANCHOR position according to checked radio button*/
    /*goalkeep always in same place column*/

    .gk {
        grid-area: 5 / 1;
    }

    /*4-3-3*/
    #f433:checked ~ .pitch {
        .lb {
            grid-area: 2 / 2;
        }
        .lcb {
            grid-area: 4 / 3;
        }
        .rcb {
            grid-area: 6 / 3;
        }
        .rb {
            grid-area: 8 / 2;
        }

        .lm {
            grid-area: 2 / 5;
        }
        .cm {
            grid-area: 5 / 5;
        }
        .rm {
            grid-area: 8 / 5;
        }

        .lw {
            grid-area: 2 / 7;
        }
        .st {
            grid-area: 5 / 7;
        }
        .rw {
            grid-area: 8 / 7;
        }
    }

    /*4-4-2*/
    #f442:checked ~ .pitch {
        .lb {
            grid-area: 2 / 2;
        }
        .lcb {
            grid-area: 4 / 3;
        }
        .rcb {
            grid-area: 6 / 3;
        }
        .rb {
            grid-area: 8 / 2;
        }

        .lm {
            grid-area: 2 / 5;
        }
        .cm {
            grid-area: 5 / 5;
        }
        .rm {
            grid-area: 8 / 5;
        }

        .lw {
            grid-area: 2 / 7;
        }
        .st {
            grid-area: 5 / 7;
        }
        .rw {
            grid-area: 8 / 7;
        }
    }

    #f352:checked ~ .pitch {
        .lb {
            grid-area: 3 / 2;
        }
        .lcb {
            grid-area: 5 / 2;
        }
        .rb {
            grid-area: 7 / 2;
        }

        .lw {
            grid-area: 2 / 4;
        }
        .lm {
            grid-area: 3 / 5;
        }
        .rcb {
            grid-area: 5 / 4;
        }
        .rm {
            grid-area: 7 / 5;
        }
        .rw {
            grid-area: 8 / 4;
        }

        .cm {
            grid-area: 4 / 7;
        }
        .st {
            grid-area: 6 / 7;
        }
    }

    #f4231:checked ~ .pitch {
        .lb {
            grid-area: 2/2;
        }
        .lcb {
            grid-area: 4/3;
        }
        .rcb {
            grid-area: 6/3;
        }
        .rb {
            grid-area: 8/2;
        }

        .lm {
            grid-area: 2/4;
        }
        .rm {
            grid-area: 8/4;
        }

        .lw {
            grid-area: 2/7;
        }
        .cm {
            grid-area: 5/5;
        }
        .rw {
            grid-area: 8/7;
        }

        .st {
            grid-area: 5/7;
        }
    }

    #f532:checked ~ .pitch {
        .lb {
            grid-area: 2/2;
        }
        .lcb {
            grid-area: 2/2;
        }
        .rcb {
            grid-area: 7/3;
        }
        .rb {
            grid-area: 8/2;
        }
        .lm {
            grid-area: 3/3;
        }

        .lw {
            grid-area: 2/5;
        }
        .rm {
            grid-area: 8/5;
        }
        .rw {
            grid-area: 5/5;
        }

        .cm {
            grid-area: 4/7;
        }
        .st {
            grid-area: 6/7;
        }
    }

}

@layer controls {
/_ copied from this nav demo
https://codepen.io/cbolson/pen/RNRxJje?editors=1000 _/
.controls {
--controls-item-spacing: 1rem;
--controls-item-radius: 3px;
--controls-item-color: var(--clr-text);
--controls-item-color-hover: white;
--controls-indicator-clr: #38a352;
--controls-transition-duration: 200ms;
--controls-trans-delay: 00ms;
--controls-transition-easing: ease-in-out;

        display: flex;
        /*flex-direction: var(--controls-flex-direction, column );*/
        justify-content: center;
        gap: var(--controls-gap);
        padding-block-start: 5rem;
        padding-inline: var(--controls-padding-inline, 1rem);

        @media (width > 400px) {
            --controls-transition-duration: 350ms;
            --controls-trans-delay: calc(var(--controls-trans-duration) * 1.25);
            --controls-flex-direction: row;
            --controls-padding-inline: 0;

            @supports not (position-anchor: --test) {
                /*fallback for browsers that don't support position-anchor */
                --border-bottom: 1px solid var(--controls-indicator-clr);
            }

            @supports (position-anchor: --test) {
                anchor-name: --hovered-option;
                &::before {
                    content: '';
                    position: absolute;
                    position-anchor: --hovered-option;
                    top: anchor(top);
                    left: anchor(left);
                    bottom: calc(anchor(top) - 1px);
                    z-index: 1;
                    background: var(--controls-indicator-clr);

                    pointer-events: none;
                    border-radius: var(--controls-item-radius)
                        var(--controls-item-radius) 0 0;
                    opacity: 1;
                    transition-property: left, right, top, button, opacity;
                    transition-timing-function: var(
                        --controls-transition-easing
                    );
                    transition-delay:
                        var(-- controls-trans-delay),
                        var(-- controls-trans-delay), 0ms, 0ms,
                        var(--controls-trans-delay);
                }

                &:has(label.hover)::before {
                    /*reverse delays*/
                    transition-delay:
                        0ms, 0ms, var(--controls-trans-delay),
                        var(--controls-trans-delay), 0ms;
                    /*opacity: 75;*/
                    bottom: anchor(bottom);
                }
            }
        }

        .controls > label {
            place-self: start;
            flex-basis: 0;
            z-index: 2;
            position: relative;
            cursor: pointer;
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 300;
            text-wrap: nowrap;
            color: var(--controls-item-color);
            padding: 0.25rem 0.5rem;
            border-radius: var(--controls-item-radius);
            transition-property: background-color, color, border-color;
            transition-timing-function: ease-in-out;

            &:hover {
                color: var(--controls-item-color-hover);
                @supports (position-anchor: --test) {
                    /*set anchor name for nav indicator*/
                    anchor-name: --hovered-option;
                }
            }

            @supports not (position-anchor: --test) {
                /*fallback for browsers that don't support position-anchor */
                position: relative;
                &::before {
                    content: '';
                    position: absolute;
                    inset: 0;
                    z-index: -1;
                    background: var(--controls-indicator-clr);
                    pointer-events: none;
                    border-radius: var(--controls-item-radius)
                        var(--controls-item-radius) 0 0;
                    pointer-events: none;
                    border-radius: var(--controls-item-radius)
                        var(--controls-item-radius) 0 0;
                    transform-origin: bottom;
                    transition-property:
                        left, right, top, button, opacity, scale;
                    transition-duration: var(--controls-transition-duration);
                    transition-timing-function: var(
                        --controls-transition-easing
                    );
                    scale: 1 0;
                }

                &:hover::before {
                    scale: 1;
                }
            }
        }

        /*current*/
        #f433:checked ~ .controls label:nth-child(1),
        #f442:checked ~ .controls label:nth-child(2),
        #f352:checked ~ .controls label:nth-child(3),
        #f4231:checked ~ .controls label:nth-child(4) {
            border-color: var(--controls-indicator-clr);
        }
    }

}

/_general styling not relevant for this demo_/

@layer base { \* {
box-sizing: border-box;
}
}

:root {
color-scheme: light dark;
--bg-dark: rgb(24, 24, 27);
--txt-light: rgb(248, 244, 238);
--txt-dark: rgb(10, 10, 10);
--line-light: rgba (0 0 0 / 0.25);
--line-dark: rgba (255 255 255 / 0.25);

    --clr-bg: light-dark(var(--bg-light), var(--bg-dark));
    --clr-txt: light-dark(var(--txt-light), var(--txt-dark));
    --clr-lines: light-dark(var(--txt-light), var(--line-dark));

}

body {
background-color: var(--clr-bg);
color: var(--clr-txt);
margin: 0;
padding: 2rem;
font-family: 'Jura', sans-serif;
font-size: 1rem;
line-height: 1.5;
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
gap: 4rem;
container-type: normal;

    --supports-warning-show: 0;
    --supports-warning-animation: '';
    --supports-warning-scroll: '';

    /*
    	@supports not (animation-timeline: auto) {
        --supports-warning-show: 1;
        --supports-warning-animation: "\A animation-timeline";
      }
    	*/
    /*
    	@supports not (scroll-marker-group: after) {
        --supports-warning-show: 1;
        --supports-warning-scroll: "\A  ::scroll-*";
    	}
    	*/

    @container style(--supports-warning-show: 1) {
        &::before {
            content: 'Missing support for: ' var(--supports-warning-animation)
                var(--supports-warning-scroll);
            position: fixed;
            top: 1rem;
            left: 50%;
            translate: -50% 0;
            font-size: 0.8rem;
            color: red;
            z-index: 999;
            white-space: pre-wrap;
        }
    }

}

h1 {
margin: 0;
font-size: 1.2rem;
}

.visually-hidden {
position: absolute;
width: 1px;
height: 1px;
padding: 0;
margin: -1px;
overflow: hidden;
clip: rect(0, 0, 0, 0);
clip-path: inset(50%);
white-space: nowrap;
border: 0;
}
