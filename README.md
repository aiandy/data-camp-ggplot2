# data-camp-ggplot2-part2
Plot 1: The code on the right builds a jittered plot of vocabulary against education of the Vocab data frame.

Add a stat_smooth() layer with method set to "lm". Make sure no CI ribbons are shown by setting se to FALSE.
Plot 2: We'll just focus on the linear models from now on.

Copy the previous command, remove the geom_jitter() layer.
Add the col aesthetic to the ggplot() command. Set it to factor(year).
Plot 3: The default colors are pretty unintuitive. Since this can be considered an ordinal scale, it would be nice to use a sequential color palette.

Copy the previous command, add scale_color_brewer() to use a default ColorBrewer. This should result in an error, since the default palette, "Blues", only has 9 colors, but we have 16 years here.
Plot 4: Overcome the error by using year as a numeric vector. You'll have to specify the invisible group aesthetic which will be factor(year). You are given a scale layer which will fix your coloring, but you'll need to make the following changes:

Add group inside aes(), set it to factor(year).
Inside stat_smooth(), set alpha equal to 0.6 and size equal to 2.

# Plot 1: Jittered scatter plot, add a linear model (lm) smooth:
ggplot(Vocab,aes(x=education,y=vocabulary))+geom_jitter(alpha=0.2)+stat_smooth(method="lm",se=F)

# Plot 2: Only lm, colored by year
ggplot(Vocab,aes(x=education,y=vocabulary,col=factor(year)))+stat_smooth(method="lm",se=F)

# Plot 3: Set a color brewer palette
ggplot(Vocab,aes(x=education,y=vocabulary,col=factor(year)))+stat_smooth(method="lm",se=F)+scale_color_brewer()

# Plot 4: Add the group, specify alpha and size
ggplot(Vocab, aes(x = education, y = vocabulary, col=year,group = factor(year))) +
  stat_smooth(method="lm",se=F,alpha=0.6,size=2) +scale_color_gradientn(colors = brewer.pal(9,"YlOrRd"))
