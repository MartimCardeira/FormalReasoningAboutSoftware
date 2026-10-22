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
| `eqblist l1 l2` | | list equality test, bool (yours) |
| `nth_bad l n` | | n-th element, `42` if out of range (the bad version) |
| `natoption` (`Some n`, `None`) | | optional nat |
| `nth_error l n` | | `Some a` or `None` |
| `option_elim d o` | | value inside `o`, or `d` for `None` |
| `hd_error l` | | `Some h` or `None` (yours) |

## Bags (a bag is a `natlist`)
| Name | Meaning | Status |
|---|---|---|
| `bag` | `Definition bag := natlist` | defined |
| `count v s` | occurrences of `v` in `s` | yours |
| `add v s` | `v :: s` | yours |
| `sum`, `member`, `remove_one`, `remove_all`, `included` | | not done (3-star, optional) |

## Ids and partial maps (Lists.v)
| Name | Meaning |
|---|---|
| `id` / `Id n` | wrapper around a nat, used as a key |
| `eqb_id x1 x2` | key equality test, bool |
| `partial_map` | `empty` or `record i v m`, like a list of (key, value) |
| `update d x v` | `record x v d` (shadows old entry, no deletion) |
| `find x d` | `None` for `empty`, otherwise first matching record |

## Modules
`.v` files are modules (`LF.Basics`, `LF.Induction`, `LF.Lists`). Blocks inside `Lists.v`: `NatList`, `PartialMap`. Blocks in `Basics.v`: `Playground`, `TuplePlayground`, `NatPlayground`, `NatPlayground2`, `LateDays`. Names defined inside a block do not leak out.

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
| `rev_length` | `length (rev l) = length l` | Lists |
| `app_nil_r` | `l ++ [] = l` | Lists (yours) |
| `rev_app_distr` | `rev (l1 ++ l2) = rev l2 ++ rev l1` | Lists (yours) |
| `rev_involutive` | `rev (rev l) = l` | Lists (yours) |
| `app_assoc4` | four-list associativity | Lists (yours) |
| `eqblist_refl` | `true = eqblist l l` | Lists (yours) |
| `count_member_nonzero` | `1 <=? count 1 (1 :: s) = true` | Lists (yours) |
| `leb_n_Sn` | `n <=? S n = true` | Lists |
| `rev_injective` | `rev l1 = rev l2 -> l1 = l2` | Lists (yours) |
| `option_elim_hd` | `hd default l = option_elim default (hd_error l)` | Lists (yours) |
| `eqb_id_refl` | `eqb_id x x = true` | Lists (yours) |
| `update_eq` | `find x (update d x v) = Some v` | Lists (yours) |
| `update_neq` | `eqb_id x y = false -> find x (update d y o) = find x d` | Lists (yours) |

Skipped (3-star or advanced, not required): `nonzeros_app`, `remove_does_not_increase_count`, `involution_injective`, `bag_count_sum`.

## Tactic patterns
| Pattern | Use |
|---|---|
| `destruct x as [\| n']` | case split, no IH. One part per constructor. Pairs: `destruct p as [n m]`. |
| `induction n as [\| n' IHn']` | case split plus IH in the recursive case |
| `simpl. rewrite -> IH. reflexivity.` | typical inductive step |
| `assert (H : P).` | prove a side fact first (two goals) |
| `replace (t) with (u).` | swap a named subterm (side goal `u = t`) |
| `discriminate H.` | close a case where `H` equates two different constructors (`simpl in H` first) |
| `intros l1 l2.` first | needed before `rewrite` when variables are still under a `forall` |

## Look things up in Coq
```coq
Print plus.        (* definition *)
Check add_comm.    (* statement of a theorem *)
Locate "+".        (* what a notation means *)
Search (_ + 0).    (* find theorems matching a pattern *)
```
