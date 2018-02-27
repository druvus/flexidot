# FlexiDot: Highly customizable ambiguity-aware dotplots for visual sequence investigation

![alt text](https://github.com/molbio-dresden/flexidot/blob/master/images/Selfdotplots_banner4.png "FlexiDot self dotplots")

FlexiDot is a cross-platform dotplot suite generating high quality self, pairwise and all-against-all visualizations by exact matching. To improve dotplot suitability for comparison of consensus and error-prone sequences, FlexiDot harbors routines for strict and relaxed handling of ambiguous residues. Our two custom shading modules facilitate dotplot interpretation and motif identification by adding information on sequence annotations and sequence similarities to the images. Combined with collage-like outputs, FlexiDot supports simultaneous visual screening of a large sequence sets, allowing dotplot use for routine screening.

## Implementation

FlexiDot is implemented in Python 2.7, using 

* [numpy](https://pypi.python.org/pypi/numpy)
* [matplotlib](https://pypi.python.org/pypi/matplotlib)
* [biopython](https://pypi.python.org/pypi/biopython)
* [colour](https://pypi.python.org/pypi/colour)

Upon first starting FlexiDot, the program tries to call all needed modules. If absent, it installs them automatically via the Python’s install manager pip. If this fails, please try again with administrator privileges.

## General FlexiDot command

```
python flexidot.py -i input.fas [optional arguments]
```

## Plotting modes

FlexiDot allows sequence investigation in three run modes via the option `-p/--plotting_modes`: 

`-p 0`    self sequence comparison 
`-p 1`    pairwise sequence comparison
`-p 2`    all-to-all sequence comparison


### Self dotplots

In self dotplot mode, each sequence is compared with itself. The resulting dotplots can be combined to form a collage [default] or written to separate files.

![alt text](https://github.com/molbio-dresden/flexidot/blob/master/images/Selfdotplots_banner.png "FlexiDot self dotplots")

```
python flexidot.py -i test-seqs.fas -p 0 -D y -f 1 -k 10 -w y -r y -x n -m 6 -P 15 -g example.gff3 -G gff_color.config
```


### Pairwise comparisons

text text text

### All-against-all comparisons

In all-against-all mode, FlexiDot compares each pair from a set of input sequences. To enable the identification of long shared subsequences at a glance, FlexiDot offers similarity shading (switched on/off via option `-x/--lcs_shading`) based on the LCS length in all-against-all comparisons. Longer matches are represented by darker background shading. 

<img src="https://github.com/molbio-dresden/flexidot/blob/master/images/all_against_all.png" width="500">

```
python flexidot.py -i test-seqs.fas -p 2 -D y -f 0 -t y -k 10 -w y -r y -x y -y 0
```

## Major features

### Ambiguity handling

`-w/--wobble_conversion Y/N`

FlexiDot handles base ambiguities, often found in consensus sequences. This allows the comparison of species-specific representations of multigene or repeat families as well as common variants or sequence subfamilies. 

<img src="https://github.com/molbio-dresden/flexidot/blob/master/images/ambiguities.png" width="500">

```
Panel A>> python flexidot.py -i Seq4.fas -p 0 -D y -f 0 -t y -k 10 -w n -r y -x n
Panel B>> python flexidot.py -i Seq4.fas -p 0 -D y -f 0 -t y -k 10 -w y -r y -x n
```


### Annotation-based shading

text text text

### Similarity shading

text text text

