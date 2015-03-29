# Create various image sizes from originals.
# We don't know ahead of time what all the image names will be.
# We will use the same image name in each folder. This may lead to some confusion but it can also be easier for selecting image sizes.
#
# These make rules will determine the names of the targets by looking at the names of the sources (prerequisites).
#
# It would be better to use the batch processing power of ImageMagick for as that could save on overheads but my make skills are very basic.
# Also, is it actually a problem right now that can not be fixed later without great expense, and is there evidence to prove that in these circumstances there is a tangible benefit to batching? 

CONVERT=C:\Program Files\ImageMagick-6.8.0-Q16\convert
CONVERTFLAGS=-resize

_width=70
_height=50
thumbs_width=83
thumbs_height=55
article_width=320
article_height=240
medium_width=640
medium_height=480
large_width=1600
large_height=1200
slideshow_width=760
slideshow_height=280

image_size=thumbs article medium large slideshow

.PHONY : all $(image_size) 

.SECONDEXPANSION:

all:$(image_size)

$(image_size):$$(patsubst originals/%,$$@/%,$$(wildcard originals/*))

#Definitely can not generate originals from anything else so make this it a final rule (double colon).
#There is the potential for programmatically generated images but that's not today's requirement.
%.jpg:: originals/$$(@F)
	$(CONVERT) $(subst /,\\,$^) $(CONVERTFLAGS) $($(@D)_width)x$($(@D)_height) $(subst /,\\,$@)
