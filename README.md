# PBChance
PBChance Component for LiveSplit

## What it is:

PBChance is a LiveSplit component that displays the chance of obtaining a PB on your current run. Whenever you reset or split, it runs 10,000 simulations by randomly drawing the remaining splits from your splits in previous attempts, and computes how many of those would result in a PB.

## Development

Terrible, but here's what worked for me:

1. Get a copy of the old Visual Studio 2017 or otherwise be able to use .NET 4.6.1
2. `git clone` PBChance but also  separatey clone LiveSplit itself
3. Open PBChance in VS
4. Add projects Livesplit.Core and UpdateManager from LiveSplit
5. Let PBChance reference them
6. Let Livesplit.Core reference UpdateManager
7. Rebuild PBChance. Solve errors but if there aren't any, a PBChance.dll path will be displayed for PBChance in a debug folder
8. Copy PBChance.dll into your LiveSplit Components folder. The one you actually want to run with an exe
9. Run livesplit.exe and see if the plugin worked.
10. Slowly iterate on 7-10 as you make changes.

## Installation:

1. Place PBChance.dll into the Components directory of your LiveSplit installation.
2. Open LiveSplit. Right click -> Edit Layout -> [Giant "+" Button] -> Information -> PB Chance
3. You can configure how many of your most recent attempts will be used to calculate the PB chance. Go to Layout Settings and click on the PB Chance tab. You can either have it use a percentage of your most recent attempts, or just a fixed number of your most recent attempts.
4. Speedrun!

## Pictures:

[The component in action.](http://i.imgur.com/YIjln5P.png)

[The configuration screen.](http://i.imgur.com/CgUuB46.png)

## Troubleshooting:

**It always displays "0%" or "-"**

You may need to configure the plugin to use a different number of attempts. For instance, it may not be reading any attempts in which you've completed a run. Additionally, you may have reset your split data at some point, which will remove the data necessary for PBChance to calculate its probability. If you want to debug the issue, try opening your splits file in a text editor (it's XML formatted). You may be able to spot missing splits, and it will inform you how to configure the PBChance component.

## Andrew's Roadmap

### next version
- Show multiple percentages for different targets
- Add a new "Goal" and WR targets
- Show live updating percentages based on the previous sample between gold and split times

### further ideas
- Fit samples to a curve and use the curve for estimates
- Use some sort of wide prior for when we have a very low sample size
- Use "on a roll" biased samples that aren't fully independent so that many-split runs don't always start with such low probabilities
