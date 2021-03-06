# The renaissance of cryptography

> > Crypto - 300pts
> 
> As time moves on, the cryptography evolves too.
> 
> Are you able to help us decipher this?
> 
> ```
> VmESauy{qswjaddiemptaq_tymdtahvxtzn_uwqlpcs_uoo_fp_sajr}
> ```

## Writeup

Given the cipher text:
`VmESauy{qswjaddiemptaq_tymdtahvxtzn_uwqlpcs_uoo_fp_sajr}`

This is a polyalphabetic substitution cipher - specifically a vigenere cipher.
Use knowledge of flag format to execute a known-plaintext attack and use the extracted key to decrypt the flag.
The known plaintext will reveal the key `BELLASO`.


Using [dcode](http://www.dcode.fr/vigenere-cipher), the cipher text can be dercypted, yielding the flag:

`UiTHack{polyalphabetic_substitution_ciphers_can_be_hard}`
