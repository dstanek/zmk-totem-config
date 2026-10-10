# Positional home row mods — trial and follow-ups

Started 2026-10-10 on both keyboards. The Totem's home row mods moved from
`&mt` (tap-preferred) to two positional hold-taps, `hml` and `hmr`, in
`config/totem.keymap`; kanata's moved from `tap-hold` to
`tap-hold-opposite-hand-release`. This file tracks what to watch while trying
it and what still needs changing if it stays.

## What changed

- `hml` (A S F V) and `hmr` (J L ; M): `balanced` flavor,
  `hold-trigger-key-positions` set to the other hand plus all six thumbs,
  `hold-trigger-on-release`. Timings copied from `&mt`: tapping term 220,
  quick-tap 100, prior-idle 100.
- D and K stay on `&lt SYM` (tap-preferred). Positional resolution is wrong
  for a layer key on a common letter: "do" would hold SYM and type `9`.
- `&mt` itself is unchanged and still serves the Backspace thumb and `;` on
  SYM.
- Kanata (satori, `kanata.kbd`): a `defhands` block (alphas, number row and
  punctuation) and `tap-hold-opposite-hand-release` on the same eight keys,
  with `(timeout hold)`, `(same-hand ignore)`, `(tap-repress-timeout
  $quick-tap)` and the thumb row plus Tab as `(neutral hold)`. The global
  prior-idle (150) still applies. D, K, Caps and the thumbs are unchanged.
- The keymap-compare template (satori) learned `&hml` and `&hmr`.

## What to watch while testing

- **Should feel better:** opposite-hand chords fire without waiting the
  220 ms term — Ctrl+J/L from F, Shift from A or `;` for a capital on the
  other hand, Cmd+key from V or M.
- **Should be unchanged:** same-hand chords still need the mod held past
  220 ms (Cmd on V + C, Shift on A + T). Stacked mods on one hand (A+F for
  Shift+Ctrl) should still work.
- **New risk:** a fast roll across hands at the *start* of a word, where the
  first key is still down when the second comes up, now becomes a mod — "fl"
  as Ctrl+L, "aj" as Shift+J. Mid-word rolls are protected by the 100 ms
  prior-idle; the first letter after a pause is not.
- If start-of-word misfires show up, raise `tapping-term-ms` on `hml`/`hmr`
  (urob's "timeless" setup uses 280). It only slows same-hand chords now.
  On kanata the knob is `hold-time` in `defvar`.
- **Kanata-only difference:** ZMK settles a same-hand key when it is
  released (as a tap); kanata's `same-hand ignore` skips it and keeps
  waiting. So a slow same-hand overlap — A held past 220 ms while S is
  pressed and released — types `S` on the laptop and `as` on the Totem.
  If that bites, `(same-hand tap)` fixes it but stops same-hand mod stacking
  on the laptop.
- Kanata also counts the number row and punctuation as hand keys, which the
  Totem doesn't have, so Ctrl+1 or Cmd+[ resolve early too.

## If it stays

- [ ] **Kanata.** Already mirrored for the trial. Tick Step 7c in
      `KBMAP.md` (marked as on trial) and keep or drop it with the Totem.
- [ ] **`;` on SYM** (`&mt RSHFT RBKT`). Still a tap-preferred Shift on the
      right home row. Switching to `&hmr RSHFT RBKT` makes Shift+left-hand
      digits (`! @ # $ %`) fast too. Kanata's `@srb` would follow.
- [ ] **Backspace thumb** (`&mt LGUI BSPC`). Probably leave. A thumb is used
      with both hands, so a by-hand rule doesn't fit; the alternative is plain
      `balanced` with no positions, which is a separate decision.
- [ ] **`&mt` block.** Once the above settle, it only covers the Backspace
      thumb (and `;` on SYM if that stays). Update its settings or comment if
      that makes them misleading.
- [ ] **Totem `&lt` comment** says layer taps mirror the kanata opt-outs.
      Still true; recheck it after the kanata change.
- [ ] Delete this file once everything is done or reverted.

## If it doesn't

Swap `&hml`/`&hmr` back to `&mt` in the base layer and delete the two
behaviors. In kanata, put the eight aliases back to
`(tap-hold $quick-tap $hold-time <key> <mod>)` and delete `defhands`. The
template's `&hml`/`&hmr` case is harmless to leave.
