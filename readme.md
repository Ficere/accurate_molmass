# Accurate Molecular Mass

This is a simple Python script that calculates the molecular mass of a molecule given its chemical formula. 

Modified from the original script from [cgohlke/molmass](https://github.com/cgohlke/molmass).

## Installation

```bash
pip install git+https://github.com/Ficere/accurate_molmass.git
```

## Usage

You can refer to the original [cgohlke/molmass](https://github.com/cgohlke/molmass).

The main modification is the EnhancedFormula class, which uses decimal.Decimal improve the floating point precision.

It is more accurate but slower than the original formula.

See the example below:

```python
from accurate_molmass import EnhancedFormula

f = EnhancedFormula("C6H12O6")
print(f.mass) # natural mass considering isotopes
print(f.isotope.mass) # Mass of isotope composed of most abundant elemental isotopes. same as f.monoisotopic_mass

adduct = EnhancedFormula("H-")
f_adduct = f + adduct
print(f_adduct.mass)
print(f.mz) # mass/charge ratio
print(f_adduct.isotope.mass)

adduct = EnhancedFormula("Na+")
f_adduct = f + adduct
print(f_adduct.mass)
print(f_adduct.isotope.mass)
```