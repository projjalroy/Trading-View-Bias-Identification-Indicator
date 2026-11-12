I built ict_htf_bias_erl_irl.pine (Pine v5). To use it, paste it into the TradingView Pine Editor and click “Add to chart”. I haven’t compiled it in TradingView, so if you get a compile error, send it to me and I’ll fix it.

How it follows your method

Bias TF	Confirms on	Entry TF
Monthly	D1	H1 / M5
Weekly	H4	M15 / M1
Daily	H1	M5
H4	M15	M1

The confirm timeframes are editable in the settings.

ERL>IRL: Price sweeps a bias-TF swing low (SSL) or swing high (BSL), which arms the setup. A bullish or bearish MSS or CISD on the confirm TF, formed after the sweep, confirms the bias. The draw on liquidity (DOL) is the most recent unfilled FVG on the bias TF in the direction of bias. Your example works this way: Monthly SSL sweep, Daily MSS or CISD, bullish bias, DOL at the Monthly FVG above.
IRL>ERL: Price taps a bias-TF FVG (a bullish FVG for bullish, a bearish FVG for bearish), then the confirm TF gives an MSS or CISD. The DOL is the external liquidity: the last swing high for bullish, the last swing low for bearish.
Model switch: You can run ERL>IRL, IRL>ERL, or both.

What you’ll see on the chart

Labels for sweeps and taps, a dotted line at the swept level, and the confirmed-bias label.
A dashed DOL line with a label, plus a box on the FVG when the DOL is an FVG.
A dashboard showing bias, status and DOL for Monthly, Weekly, Daily and H4.
Optional alerts for sweeps, taps and confirmed bias.

How I defined the terms (all adjustable in the code)

MSS: a close beyond the last confirmed swing high or low on the confirm TF.
CISD: a close beyond the open of the last opposing run of candles.
Bias ends when:
the DOL is reached;
price closes beyond the sweep extreme (ERL) or beyond the FVG (IRL);
the setup expires (default 12 bias-TF bars).
No repainting: All higher-timeframe data comes from closed bars only.

Limits

Set your chart to a timeframe at or below the confirm TF (for example H1 or lower for Daily bias). If it’s higher, the dashboard row says so and that module doesn’t run.
The indicator tracks only the latest unfilled bullish and bearish FVG per bias TF, not a full list. If neither is on the correct side of price, the DOL falls back to the external swing.
Because Monthly and Weekly history is limited on low timeframes, back-testing those modules needs a lot of bars.
