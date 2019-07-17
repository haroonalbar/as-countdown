# as-countdown

![][image_ref]

This package provides a custom element `<as-countdown />` that counts down to a given date or timestamp. Per default the component displays the remaining days, hours, minutes and seconds. For each of these a label is displayed. The labels default to *Days*, *Hours*, *Minutes* and *Seconds*. All customizations can be found [here](./src/components/countdown/readme.md).

## Usage

```html
<as-countdown
  date="2019-12-24">
</as-countdown>

<as-countdown
  date="1563369146414"
  days-label="Dias"
  hours-label="Horas"
  minutes-label="Minutos"
  seconds-label="Segundos">
</as-countdown>

<as-countdown
  date="1566346414104"
  hide-seconds>
</as-countdown>

<as-countdown
  date="2019-12-31"
  days-label="Days left in 2019"
  hide-hours
  hide-minutes
  hide-seconds>
</as-countdown>
```

## Installing

### via script tag

- Put a script tag similar to this `<script src='https://unpkg.com/as-countdown@0.0.1/dist/as-countdown.js'></script>` in the head of your index.html
- Then you can use the element anywhere in your template, JSX, html etc

### via node modules
- Run `npm install as-countdown --save`
- Put a script tag similar to this `<script src='node_modules/as-countdown/dist/as-countdown.js'></script>` in the head of your index.html
- Then you can use the element anywhere in your template, JSX, html etc

Find more details on integrations into frameworks [here](https://stenciljs.com/docs/overview).

## Styling

The component does not make any assumptions about stylings and displays the countdown as an inline element. You are free to style it in every way you want. Use these css selectors to apply styles accordingly:

```css
as-countdown { /* root */ }
as-countdown > section { /* sections (days, hours, minutes, seconds) */ }
as-countdown > section > div { /* value for respective section */ }
as-countdown > section > label { /* label for respective section */ }
```

## The done event

When the countdown has finished a *done* event is being dispatched. You can react to it like this:

```js
const countdownEl = document.querySelector('as-countdown');

countdownEl.addEventListener('done', () => {
  /* Do whatever needs to be done */
});
```

If you use a JS framework you can use that framework's default event binding syntax. Here's an example for *Angular*:

```html
<as-countdown
  date="2019-12-24"
  (done)="decorateChristmasTree()">
</as-countdown>
```

## Behaviour

*Fallback behaviour: Component shows 0 Days, 0 Hours, 0 Minutes and 0 Seconds.*

- The `date` can be passed in as a timestamp or ISO string. Invalid dates will trigger the fallback behaviour
- Dates in the past will trigger the fallback behaviour

[image_ref]:
data:image/png;base64,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MS547IorrkiZ4vjx41UYhEv1admypRl/5MiRKcPZxX/sscfMuNm4cdVVV6nyHnHEEWmzj3LalV/vS3cN0iYc4YNr1qyJHXrooWnL/cILLySUgBV67IADDkgb5+23306Ik09/Crsfe/fuHfvzzz/zCUnkylqcb+qMhS8erVq1iu644w765JNPCk3nyy+/VGFOPPFEatu2rW34mjVrmvvxJO/Xr5/5325j3rx5piVUv359uyCR37d+/Xp6+umniRVvoXl9//33iRW5CgdWDz/8sLJ4vv76a7ryyisJrZTHH3+cLr/8cjrhhBMKTS8bAuzatUu1FuDKgYwYMYLOPPNMYuVLc+fOpcGDB6v9KPMZZ5yhrEHsuOSSS+jXX39Vx+6++24655xzCFb45MmT1QcHOnXqRGBXqlQpFS5fvlBm8IGA40MPPaTqERizYUT/+9//lBXdqlUr6tGjR75giV45M31knH/++baWSTrrrWvXrirO6NGjMz1tQrzNmzebFtIjjzyScCwb/tx7771m/rlmmDzTWdCaOyxDvskSirlp0yYzjeHDhyccy+Y/U6dONcs1bty4AkWZOHGieVzXre+//97c17NnzwJxdGsF3JcvX17geK7vsJb/s88+Sygu92vETj75ZMUvXV1MiCR/AiGQsQ/6888/d/204Yqg4tSuXdt13OQITIMuu+wyZSF16dKF+vbtmxwk8v+//fZb08Jzkln4U6dNm6aC3njjjVStWrWEaFWqVCFW+nT11VeTtSWSECgL/7ACNXNtZ81169bNPP7BBx+obXaJmPs6d+5sbusN+K21bNu2TW/mze+bb76pysoPL0ru84Af+rrrrlPHv/nmG9L3bd7AiVBBM1bQuMBssZkf9g+mLRYU6ocffqjCHH300eoXzc8ff/wxbbxUB9mSotmzZ6vmGZr52Shs5Zr8wJJbGGmLYVVUvXr1MsNae95vuOEG1Vy1U2RmhCzbgJKANGzYkPbff/8CuUfntBa43SCVKlXSu+jTTz81t/XGjBkz9Cadeuqp5nY+bICRdkkmK2dd/urVq+tNstY7c6dshEIgYwVdvnx5gsWmPyVKlEibYXZHmMehUI866igqW7YsHXLIIcpnCAvYqSUD611bzFByFStWNNPOpg2UX/PDL/6nk3fffdc8DG7wvTZp0kT1vGM0w3nnnUeLFy82w+TKBrst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CIEcIZCxgu7UqRMVL16cjj/+eJo2bVqhOH777TcaOXKkCteiRQuaOnUqnXzyyVShQgVq3749TZgwQR2Dcn733XdTpgcF/s0336Q8LgeEgBAQArlCoHimBfn8889dRV24cCFt3bpVxYF7olSpUgnx27VrRwMGDKBYLEZlypRJOKb/QIm/9NJLytqGm+T+++/Xh+RXCAgBIZBzBDJW0G+++Sbt2bPHBNKoUSNTAZs7LRvwG0OOOOIIOv30080j8Evvs88+VLJkSRo7dqy5P3kDD4RLLrlE7X7yySdp27ZtyUHkvxAQAkIgpwhk7OIoX748ValSxfyUKFEiLZglS5ao4yeddBJ98cUXStkec8wxtO+++xJ+L7vsMvr6669t08CD4MILL1THevbsSRdccIFtONkpBISAEMglAhlb0G4hYLwzZO3atdS4ceOEjsA1a9YQPk899RTNnDmT4O6wym233aY6I2F9o6NRRAgIASGQDwQytqDdwvn2229VlA8//FApZ/iQX3vtNfWxDpnr3r076bCIgDD33HOPijt58mQqV66c2pYvISAEhECuEwjNgrYOnRs9ejRdd911JttWrVrRYYcdRv369VPKG0PxbrjhBuXTvuiii1Q4WNHNmjUz4zjdeP31121nKp511lnKveI0nSDDoQO1WrVqVKtWrYTTvPHGG3TIIYdQgwYNEvbrP3AJvffee3TOOecQfPQYjw4Xkl+yfv161bLB9YErCoLROJhQdMIJJ1D16tUdner333+nL7/8kmrWrElWVxhmgqIvoXbt2gn7t2/fThhOefTRR5vpY0gnhnKCUXIHsxlINoRArhHgURO+CLsfYswmxpaxbXr6OI93jvFklgJh2AWi4iON3r17q+Psbzb38Zjp2Pvvv29+rr/+evOY3s83e4F0zz777FjDhg3NsNjGhxVNgbBFtQNl5gdQgdOzQovxsMIC+/WOOXPmxE488cQYtzhi559/fowfYPqQL79jxoxR3PjhaqaHc+GcOLcT+eyzz2I82zOG647fW2+9NcYdwzEecmleE9SNDRs2xH766acYdybHeBhmrG7dumby//3vf2NggQ9YzZ8/3zwmG0IglwmE5uKAlQQ59thjTWtM7fj7C1O24ZuGwNqCwILT0rRpUzXmGuOu8YEVrkXvw9jqZJk3bx6tWrWKMDEGPmxs6w+s86pVq6oO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