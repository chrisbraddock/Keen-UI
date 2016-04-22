<template>
    <section class="section section-ui-tooltip">
        <h2 class="section-heading">UiTooltip</h2>

        <p>UiTooltip allows you to show a tooltip on an element. You can customize the position and the event the causes the tooltip to open.</p>

        <p>UiTooltip is used internally by <a href="#/ui-icon-button-demo">UiIconButton</a> and <a href="#/ui-fab-demo">UiFab</a>.</p>

        <h3>Examples</h3>

        <div class="demo">
            <div class="group the-simpsons">
                <image-pane inline-template
                    :image="simpson.image" :name="simpson.name" :position="simpson.position"
                    v-for="simpson in theSimpsons"
                >
                    <div
                        class="image-pane" v-el:portrait
                        :style="{ 'background-image': 'url(' + image + ')' }"
                    >
                        <ui-tooltip
                            :trigger="$els.portrait" :content="name" :position="position"
                        ></ui-tooltip>
                    </div>
                </image-pane>
            </div>
        </div>

        <h3>API</h3>

        <ui-tabs raised>

            <ui-tab header="Props">
                <div class="table-responsive">

                    <table class="table">
                        <thead>
                            <th>Name</th>
                            <th>Type</th>
                            <th>Default</th>
                            <th>Description</th>
                        </thead>

                        <tbody>
                            <tr>
                                <td>trigger *</td>
                                <td>HTMLElement</td>
                                <td>(required)</td>
                                <td>An Element to attach the tooltip to. By default, when this element is hovered or focused, the tooltip is shown.</td>
                            </tr>

                            <tr>
                                <td>content</td>
                                <td>String</td>
                                <td></td>
                                <td>The tooltip content (text only).</td>
                            </tr>

                            <tr>
                                <td>position</td>
                                <td>String</td>
                                <td class="no-wrap"><code>"bottom center"</code></td>
                                <td>The position of the tooltip relative to the trigger. One of <code>top left</code>, <code>left top</code>, <code>left middle</code>, <code>left bottom</code>, <code>bottom left</code>, <code>bottom center</code>, <code>bottom right</code>, <code>right bottom</code>, <code>right middle</code>, <code>right top</code>, <code>top right</code>, or <code>top center</code>.</td>
                            </tr>

                            <tr>
                                <td>openOn</td>
                                <td>String</td>
                                <td><code>"hover focus"</code></td>
                                <td>The type of event(s) that will cause the tooltip to open. One or more of <code>click</code>, <code>hover</code>, or <code>focus</code>. Separate multiple events with a space.</td>
                            </tr>
                        </tbody>
                    </table>

                </div>

                * Required prop
            </ui-tab>

        </ui-tabs>

    </section>
</template>

<script>
import UiTooltip from '../../src/UiTooltip.vue';
import UiTab from '../../src/UiTab.vue';
import UiTabs from '../../src/UiTabs.vue';

let theSimpsons = [
    {
        position: 'top center',
        name: 'Maggie Simpson',
        image: 'http://i.imgur.com/eK26qtK.jpg'
    }, {
        position: 'bottom center',
        name: 'Lisa Simpson',
        image: 'http://i.imgur.com/wIb44g9.jpg'
    }, {
        position: 'right middle',
        name: 'Bart Simpson',
        image: 'http://i.imgur.com/XkEz9zg.jpg'
    }
];

export default {
    data() {
        return {
            theSimpsons
        };
    },

    components: {
        UiTab,
        UiTabs,
        UiTooltip,

        ImagePane: {
            props: ['image', 'name', 'position'],
            components: {
                UiTooltip
            }
        }
    }
};
</script>

<style lang="stylus">
@import '../../src/styles/variables';

.section-ui-tooltip {
    .group {
        display: flex;
    }

    .image-pane {
        background-size: cover;
        background-position: 50%;
        margin-right: 16px;
        margin-bottom: 16px;

        position: relative;
    }

    .the-simpsons {
        .image-pane {
            width: 120px;
            height: 120px;
            border-radius: 8px;
        }
    }
}
</style>