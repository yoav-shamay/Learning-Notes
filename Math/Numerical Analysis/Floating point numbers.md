Saved as the form 
$\text{mantissa} \times 2^{\text{exponent}}$
For example: $0.1234 \times 10^5$.
Keeps always the same amount of digits in the manitssa.
Denote the amount of digits saved as $k$.
Has 2 methods to represent a number:
- Chopping - just take the first digits from the number, truncate the rest
- Rounding - round to the closest matching number, equivalent to adding $2^{-k}$ then truncating.
Chopping has a maximum relative error of $2^{-k+1}$. Rounding too has $2^{-k+1}$ (though in base 10 it's $5 \times 10^{-2k+1}$ instead).
This is assuming base 2.
Sometimes it's thought about as base 10, in this case replace all 2 with 10.