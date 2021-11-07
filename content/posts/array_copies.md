---
title: "Array_copies"
date: 2021-09-13
draft: true
toc: false
images:
tags:
  - untagged
---



This implementation work is direct action to gain experience, gather feedback and deal with issues as they arise. Voices of concern were raised on the SG22 mailing list ahead of the meeting; implementation experience should smoke out issues and, hopefully, allay fears.
I am a signed up (copyright assigned) FSF GNU contributor with a couple of GCC patches under my belt and good GCC contacts. I have some LLVM / Clang experience, and I’m strongly motivated to gain more (my coming contract is in compiler development).
I have been attending SG19 Machine Learning and SG22 C / C++ Liaison meetings regularly over the past year.
By early October I aim to have GCC and Clang branches publicly available with functional features. I will provide a status report ahead of the WG21 meeting in October. I will continue to provide progress reports as long as the branches are active. When ready, the branches will be made available on Compiler Explorer, for easy online experimentation.
Some aspects of the work are longer-term undertakings than this initial ‘kickstart’. In particular, ABI specification will be needed for array as a return type.

C array remains central, in C. Some array extensions were added in C99.

C++ has largely neglected C array and did not merge the C99 extensions.

The C++ standard library has higher-level array-like abstractions,
including `std::array<T,N>` as an alternative to `T[N]`.
