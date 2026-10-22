# Coq cheat sheet (LF)

Living reference of what is available. Source file and line in brackets.

## Functions on bool
| Name | Meaning | Source |
|---|---|---|
| `negb b` | not | Basics |
| `andb` / `&&` | and | Basics |
| `orb` / `\|\|` | or | Basics |

## Other types and helpers in Basics
| Name | Meaning |
|---|---|
| `day`, `next_weekday` | enumerated type and a function on it |
| `nandb`, `andb3` | nand, three-way and |
| `rgb`, `color`, `monochrome`, `isred` | colour types and tests |
| `bit`, `nybble`, `all_zero` | 4-bit values and a test |
| `letter`, `modifier`, `grade`, `comparison` | grade types (`Eq`, `Lt`, `Gt`) |
| `letter_comparison`, `modifier_comparison`, `grade_comparison` | comparisons on them |
| `lower_letter`, `lower_grade`, `apply_late_policy` | grade functions |
| `bin` (`Z`, `B0`, `B1`), `incr`, `bin_to_nat` | binary numbers (optional exercise) |

## Functions on nat
All match on the **first** argument unless noted.

| Name | Notation | Meaning | Source |
|---|---|---|---|
| `pred n` | | predecessor | Basics |
| `even n` | | matches `O`, `S O`, `S (S n')` | Basics |
| `odd n` | | `negb (even n)` | Basics |
| `plus n m` | `n + m` | `O => m`, `S n' => S (plus n' m)` | Basics |
| `mult n m` | `n * m` | `O => O`, `S n' => plus m (mult n' m)` | Basics |
| `minus n m` | `n - m` | matches both args | Basics |
| `exp b p` | | power | Basics |
| `factorial n` | | | Basics |
| `eqb n m` | `n =? m` | equality test, bool | Basics |
| `leb n m` | `n <=? m` | less-or-equal test, bool | Basics |
| `ltb n m` | `n <? m` | less-than test, bool | Basics |
| `double n` | | `S (S (double n'))` | Induction |

## Proven results (usable with `rewrite` / `apply`)
| Name | Statement | Source |
|---|---|---|
| `plus_O_n` | `0 + n = n` | Basics |
| `plus_1_l` | `1 + n = S n` | Basics |
| `mult_0_l` | `0 * n = 0` | Basics |
| `plus_id_example` | `n = m -> n + n = m + m` | Basics |
| `mult_n_0_m_0` | `p * 0 + q * 0 = 0` | Basics |
| `mult_n_1` | `p * 1 = p` | Basics |
| `plus_1_neq_0` | `((n + 1) =? 0) = false` | Basics |
| `zero_nbeq_plus_1` | `(0 =? (n + 1)) = false` | Basics |
| `negb_involutive` | `negb (negb b) = b` | Basics |
| `andb_commutative` | `andb b c = andb c b` | Basics |
| `andb3_exchange` | `andb (andb b c) d = andb (andb b d) c` | Basics |
| `andb_true_elim2` | `andb b c = true -> c = true` | Basics |
| `identity_fn_applied_twice` | `f x = x` for all x gives `f (f b) = b` | Basics |
| `andb_eq_orb` | `andb b c = orb b c -> b = c` | Basics |
| `lower_letter_lowers`, `lower_grade_lowers` | grade functions lower grades | Basics |
| `add_0_r` | `n + 0 = n` | Induction |
| `minus_n_n` | `n - n = 0` | Induction |
| `mul_0_r` | `n * 0 = 0` | Induction (yours) |
| `plus_n_Sm` | `S (n + m) = n + S m` | Induction (yours) |
| `add_comm` | `n + m = m + n` | Induction (yours) |
| `add_assoc` | `n + (m + p) = (n + m) + p` | Induction (yours) |
| `double_plus` | `double n = n + n` | Induction (yours) |
| `eqb_refl` | `(n =? n) = true` | Induction (yours) |
| `even_S` | `even (S n) = negb (even n)` | Induction (yours) |
| `mul_comm` | `m * n = n * m` | Induction |
| `leb_refl` | `(n <=? n) = true` | Induction |

## Notations
| Notation | Meaning | Notes |
|---|---|---|
| `x + y`, `x - y`, `x * y` | `plus`, `minus`, `mult` | nat |
| `x =? y`, `x <=? y`, `x <? y` | `eqb`, `leb`, `ltb` | return bool |
| `x && y`, `x \|\| y` | `andb`, `orb` | bool |
| `(x, y)` | `pair x y` | pair of nats |
| `x :: l` | `cons x l` | level 60, right associative |
| `[ ]` | `nil` | empty list |
| `[x; ...; y]` | `cons x (... (cons y nil) ...)` | list literal |
| `l1 ++ l2` | `app l1 l2` | level 60, right associative |

`1 :: 2 :: 3 :: nil` means `1 :: (2 :: (3 :: nil))`, which is `[1;2;3]`.

## Pairs and lists (Lists.v)
| Name | Notation | Meaning |
|---|---|---|
| `natprod` / `pair` | `(x, y)` | pair of nats |
| `fst p`, `snd p` | | components of a pair |
| `swap_pair p` | | `(x,y)` becomes `(y,x)` |
| `natlist` / `cons`, `nil` | `x :: l`, `[]` | list of nats |
| `repeat n count` | | list of `count` copies of `n` |
| `length l` | | `nil => 0`, `h :: t => S (length t)` |
| `app l1 l2` | `l1 ++ l2` | recurses on `l1`: `h :: (app t l2)` |
| `hd default l` | | head, or `default` for `nil` |
| `tl l` | | tail, `nil` for `nil` |
| `rev l` | | `rev t ++ [h]` |
| `nonzeros l` | | drop zeros (yours) |
| `oddmembers l` | | keep odd elements (yours) |
| `countoddmembers l` | | `length (oddmembers l)` |
| `alternate l1 l2` | | interleave (3-star, not done) |

## Bags (a bag is a `natlist`)
| Name | Meaning | Status |
|---|---|---|
| `bag` | `Definition bag := natlist` | defined |
| `count v s` | occurrences of `v` in `s` | yours |
| `add v s` | `v :: s` | yours |
| `sum`, `member`, `remove_one`, `remove_all`, `included` | | not done (3-star, optional) |

## Proven results on pairs and lists
| Name | Statement | Source |
|---|---|---|
| `surjective_pairing` | `p = (fst p, snd p)` (needs `destruct p`) | Lists |
| `snd_fst_is_swap` | `(snd p, fst p) = swap_pair p` | Lists (yours) |
| `fst_swap_is_snd` | `fst (swap_pair p) = snd p` | Lists (yours) |
| `add_inc_count` | `count v (add v s) = S (count v s)` | Lists (yours) |
| `nil_app` | `[] ++ l = l` | Lists |
| `tl_length_pred` | `pred (length l) = length (tl l)` (needs `destruct l`) | Lists |
| `app_assoc` | `(l1 ++ l2) ++ l3 = l1 ++ (l2 ++ l3)` | Lists |
| `app_length` | `length (l1 ++ l2) = length l1 + length l2` | Lists |

## Tactic patterns
| Pattern | Use |
|---|---|
| `destruct x as [\| n']` | case split, no IH. One part per constructor. Pairs: `destruct p as [n m]`. |
| `induction n as [\| n' IHn']` | case split plus IH in the recursive case |
| `simpl. rewrite -> IH. reflexivity.` | typical inductive step |
| `assert (H : P).` | prove a side fact first (two goals) |
| `replace (t) with (u).` | swap a named subterm (side goal `u = t`) |

## Look things up in Coq
```coq
Print plus.        (* definition *)
Check add_comm.    (* statement of a theorem *)
Locate "+".        (* what a notation means *)
Search (_ + 0).    (* find theorems matching a pattern *)
```
