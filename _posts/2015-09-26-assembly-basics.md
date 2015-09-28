---
layout: post
title:  "assembly basics"
categories: systems tutorial C code
---

#CPU registers
* %eax
* %edx
* %ecx
* %ebx
* %esi
* %edi
* %esp  (special)
* %ebp  (special)


# Assembly Arithmetic Instructions
* addl Src,Dest Dest = Dest + Src
* subl Src,Dest Dest = Dest - Src
* imull Src,Dest Dest = Dest * Src Signed multiply
* sall Src,Dest Dest = Dest << Src Also called shll
* sarl Src,Dest Dest = Dest >> Src Arithmetic
* shrl Src,Dest Dest = Dest >> Src Logical
* xorl Src,Dest Dest = Dest ^ Src
* andl Src,Dest Dest = Dest & Src
* orl Src,Dest Dest = Dest | Src

# leal instruction for address computation  
leal Src,Dest

* Src is indexed address mode expression
* Set Dest (must be register) to address denoted by expression

You should think of this as “Compute Using Effective Address”
