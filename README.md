## ReadableNumbers.jl
###### easily read numbers with many digits
__CORRECTED__

To Install: `julia> Pkg.clone("https://github.com/jsarnoff-juliacon/ReadableNumbers.jl")`

##### Use
```F#
using ReadableNumbers    # exports stringpretty, showpretty, 
                         # intSizer(<nDigitsPerGroup>), floatSizer(<nDigitsPerGroup>)
                         # intSpacer(<UTF8char>), floatSpacer(<UTF8char>)

# specify formatting for integers and the integer part of floats (as strings)                              
intSpacer!(','); intSizer!(3);             # integers in groups of 3 digits separated by ','

showpretty(-1234567)                       # -1,234,567

intval = 1234567
intstr = stringpretty(1234567)             # "1,234,567"
parse(Int, intstr, ',')         == intval  # true
parse(Int, intstr, intSpacer()) == intval  # true

# specify formatting constraints for the fractional part of floats (as strings)                              
floatSpacer!('_'), floatSizer!(4)          # fractionals in groups of 4 digits separated by '_'

showpretty(exp(1))
# 2.7182_8182_8459_045

stringpretty(12345.87654321)               # "12,345.8765_4321"
stringpretty(12345.87654321, ',', 3)       # "12,345.876,543,21"

floatSpacer!(intSpacer()); floatSizer(intSizer())
fltval = 12345.87654321
fltstr = stringpretty(fltval)              # "12,345.876,543,21"
parse(Float64, fltstr, ',')     == fltval  # true

floatSpacer!('_'); floatSizer!(4)
fltstr = stringpretty(fltval)              # "12,345.8765_4321"
parse(Float64, fltstr, ',', '_') == fltval # true

bigval = BigFloat(pi)
showpretty(bigval,'_',5)
# 3.14159_26535_89793_23846_26433_83279_50288_41971_69399_37510_58209_74944_59230_78164_06286_198

```
