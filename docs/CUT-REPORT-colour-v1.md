# colour-v1: first picture cut (8 Nov)

File work only. Nothing was generated, downloaded, uploaded, posted, committed or spent. No existing file under the film folder was changed. The only new files are the four in this folder. `O` = `~/israel-game/.superpowers/coordination/handover-1107/opening-film`.

- `colour-v1.mp4`: 1280x720, 24 fps, H.264 High, yuv420p, **picture only (no audio track)**. No VO and no sound bed. The sound files in `O/edit/sound/src` were not laid under it.
- `colour-v1-sheet.jpg`: one frame per cut (the middle frame), labelled with the cut number and its start time.
- `cv1-build.py`: the build script that made both files. It reads `O/clips`, `O/colour-test/v3` and `O/edit/fonts`, and writes only to this folder and to the scratch folder.

**Runtime 67.125 s (1611 frames). Map at 63.125 s (frame 1515).** The cut list had 67.5 s with the map at 63.5. The 0.375 s difference is the C28 trim (cut 34, 1.8 s to 34 frames = 1.417 s).

## Verification (ffprobe)

```
$ ffprobe -v error -count_frames -show_entries format=duration:stream=codec_name,profile,width,height,pix_fmt,r_frame_rate,nb_read_frames -of default=nw=1 colour-v1.mp4
codec_name=h264
profile=High
width=1280
height=720
pix_fmt=yuv420p
r_frame_rate=24/1
nb_read_frames=1611
duration=67.125000
```

The sum of the 34 cuts in the table below is 1611 frames = 67.125 s. That equals the ffprobe duration and the decoded frame count exactly (difference 0 frames). The build also decoded each cut's segment and checked that its frame count matched the plan before concatenating.

## Frame rounding

Cut starts are the cut list's nominal starts (after the changes below), rounded to the nearest frame at 24 fps. Durations are the differences between those starts. So a nominal 1.6 s cut can be 38 or 39 frames, and no start is more than half a frame off its nominal time. For 1x clips the source range is exactly as many frames as the cut, so the in-points below are the exact source frames used.

## Per cut

Times are in seconds. "In-out" is the source range, with the frame numbers inclusive. Fit: **fill** = scaled to 1280x720, with at most 2 % of the picture cropped; **pillarbox** = the whole frame scaled to 720 high, with black bars at the sides (the coordinator's ruling: non-16:9 v3 frames are intended, no re-crop).

| Cut | Start | Frames | Dur | File | In-out (s) | Speed | Fit | On screen |
|---|---|---|---|---|---|---|---|---|
| 1 | 0.000 | 38 | 1.583 | black card | - | - | - | "Tel Aviv. 13 May 1948." (centred) |
| 2 | 1.583 | 82 | 3.417 | clips/C1-seedance-raw.mp4 | 0.000-3.417 (fr 0-81) | 1 | fill | Lower third from 2.000 s: "The British Mandate ends at midnight, 14 May." |
| 3 | 5.000 | 19 | 0.792 | clips/C2-seedance-raw.mp4 | 2.208-3.000 (fr 53-71) | 1 | fill | - |
| 4 | 5.792 | 43 | 1.792 | clips/C4-seedance-raw.mp4 | 0.208-2.000 (fr 5-47) | 1 | pillarbox | - |
| 5 | 7.583 | 44 | 1.833 | clips/C5-seedance-raw.mp4 | 0.000-1.833 (fr 0-43) | 1 | fill | - |
| 6 | 9.417 | 52 | 2.167 | black placeholder | - | - | - | grey label: "FILM: Vienna 1938, Nitsche (USHMM RG-60.4952) / Placeholder: real film not in the folder" |
| 7 | 11.583 | 39 | 1.625 | colour-test/v3/C31-v3.png (900x675) | still, ffmpeg zoompan push 1.00 to 1.06, centred | - | 4:3 pillarbox, greyscale | - |
| 8 | 13.208 | 33 | 1.375 | colour-test/v3/C32-v3.png (2839x2129) | still, ffmpeg zoompan push 1.00 to 1.06, centred | - | 4:3 pillarbox, greyscale | - |
| 9 | 14.583 | 29 | 1.208 | black placeholder | - | - | - | "FILM: Westerbork 1944, wagon door barred (Acte 1, 06.08) / Placeholder..." |
| 10 | 15.792 | 43 | 1.792 | black placeholder | - | - | - | "FILM: Westerbork 1944, the long train leaves (Acte 1, 07.57) / Placeholder..." |
| 11 | 17.583 | 12 | 0.500 | black | - | - | - | - |
| 12 | 18.083 | 82 | 3.417 | clips/C8-seedance-raw.mp4 | 0.000-2.583 (fr 0-61) | 0.756 | fill | - |
| 13 | 21.500 | 48 | 2.000 | clips/C10-seedance-raw.mp4 | 0.000-2.000 (fr 0-47) | 1 | fill, cropped to the top 76 % (centred) | Lower third: "David Ben-Gurion. Leader of the Jews of Palestine." |
| 14 | 23.500 | 43 | 1.792 | clips/C11-retake1-raw.mp4 | 0.333-2.125 (fr 8-50) | 1 | pillarbox, 20 px cut from the right edge | - (the muzzle flash, src frame 44, lands at 25.000 s, 1.5 s into the cut) |
| 15 | 25.292 | 15 | 0.625 | clips/C13-seedance-raw.mp4 | 0.000-0.625 (fr 0-14) | 1 | pillarbox, plus an edit push 1.00 to 1.08 | - |
| 16 | 25.917 | 14 | 0.583 | clips/C14-seedance-raw.mp4 | 0.000-0.583 (fr 0-13) | 1 | pillarbox | - |
| 17 | 26.500 | 31 | 1.292 | clips/C16-seedance-raw.mp4 | 2.417-3.708 (fr 58-88) | 1 | pillarbox (portrait) | - |
| 18 | 27.792 | 34 | 1.417 | clips/C17-seedance-raw.mp4 | 0.208-1.625 (fr 5-38) | 1 | pillarbox (square) | - |
| 19 | 29.208 | 62 | 2.583 | clips/C15-retake1-raw.mp4 | 0.000-2.583 (fr 0-61) | 1 | pillarbox | - |
| 20 | 31.792 | 34 | 1.417 | clips/C18-seedance-raw.mp4 | 0.000-1.417 (fr 0-33) | 1 | pillarbox (portrait) | - |
| 21 | 33.208 | 86 | 3.583 | clips/C20b-retake1-raw.mp4 | 0.000-3.583 (fr 0-85) | 1 | fill | - |
| 22 | 36.792 | 58 | 2.417 | clips/C30-seedance-raw.mp4 | 0.000-2.417 (fr 0-57) | 1 | fill | - |
| 23 | 39.208 | 86 | 3.583 | clips/C22-seedance-raw.mp4 | 0.000-2.917 (fr 0-69) | 0.814 | fill | - |
| 24 | 42.792 | 43 | 1.792 | clips/C20b-retake1-raw.mp4 | **hold** on frame 96 (4.000 s), zoompan push 1.45 to 1.55 centred on the men at the table (x 0.56, y 0.66) | - | fill | - |
| 25 | 44.583 | 9 | 0.375 | clips/C22-seedance-raw.mp4 | 2.917-3.292 (fr 70-78) | 1 | fill | - |
| 26 | 44.958 | 97 | 4.042 | black | - | - | - | - |
| 27 | 49.000 | 86 | 3.583 | clips/C23-seedance-raw.mp4 | 0.000-3.583 (fr 0-85) | 1 | pillarbox, 2 px cut top and bottom | Lower third: "14 May 1948, 4 p.m. The State of Israel is declared." |
| 29 | 52.583 | 39 | 1.625 | black card | - | - | - | "Thirteen hours later." (centred) |
| 30 | 54.208 | 53 | 2.208 | clips/A1-seedance-comp.mp4 | 0.000-2.208 (fr 0-52) | 1 | native 1280x720 | Lower third: "Egyptian planes bomb Tel Aviv." |
| 31 | 56.417 | 31 | 1.292 | clips/B1-seedance-comp.mp4 | 0.000-1.292 (fr 0-30) | 1 | native 1280x720 | - |
| 32 | 57.708 | 43 | 1.792 | clips/C25-seedance-raw.mp4 | 0.000-1.792 (fr 0-42) | 1 | pillarbox | - |
| 33 | 59.500 | 53 | 2.208 | clips/C26-seedance-raw.mp4 | 1.833-4.042 (fr 44-96) | 1 | pillarbox | - |
| 34 | 61.708 | 34 | 1.417 | clips/C28-retake1-trim1p4.mp4 | 0.000-1.417 (fr 0-33, all of it) | 1 | pillarbox | - |
| 35 | 63.125 | 96 | 4.000 | black placeholder | - | - | - | "MAP / Placeholder: no game map capture in the folder" |

Cut 28 stays retired, as in cutlist-fixed.json. Cards and lower thirds use `O/edit/fonts/FrankRuhlLibre-Medium.ttf`: 54 px for the centred cards, 36 px for the lower thirds (with a soft drop shadow), and grey 26 px for the placeholder labels. They were drawn as PNGs with Pillow, because this ffmpeg has no drawtext, and laid over the picture with `overlay`. Only the `text` fields of the cut list are burned in. The cut list has no other captions; the VO lines are not captioned, since there is no VO.

## Deviations from cutlist-fixed.json

Owner-approved substitutions (as briefed):
1. **Cut 14:** C11 becomes `C11-retake1-raw.mp4`, src 0.333-2.125. The flash (src frame 44, 1.833 s, the one luma spike in the take) is 1.5 s into the cut, near the end of the line "...the UN declaration of partition," where the director puts the first gunshot. I also cut 20 px off the right edge: the retake has a white band about 8-10 px wide, plus a gradient, baked into its right edge on every frame.
2. **Cut 19:** C15 becomes `C15-retake1-raw.mp4`, src 0-2.583.
3. **Cut 21:** C20 becomes `C20b-retake1-raw.mp4`, src 0-3.583. **What I chose and why:** any 3.6 s window of a 4.04 s clip must cover 0.44-3.6 s, so no in-range window avoids the part after 2.0 s at full speed. Avoiding it would mean either a cut of about 2.0 s (breaking the VO line "Tomorrow at midnight, British rule ends. Washington says wait.") or a 0.56x slow-down. I kept 0-3.6 at 1x. The wall portrait's head leaves the top of frame at about 2.0 s, which is 35.2 s in the film.
4. **Cut 24:** it cannot come from C20b without overlap: cut 21 uses src 0-3.583, and only 0.46 s is left after it. It is now a **hold on C20b's last frame (frame 96, 4.000 s, outside cut 21's range) with a slow ffmpeg push**, framed on the men at the table. **FLAG:** this is a still, which breaks the owner's "no pictures" rule. Also, the "leaning man" of the old C20 cut does not exist in C20b: nobody leans. The frame is soft, because 480p is enlarged about 2.25x.
5. **Cut 34:** C28 becomes `C28-retake1-trim1p4.mp4`, all 34 frames (1.417 s). The cut is **shortened from 1.8 to 1.417 s**, so the map moves from 63.5 to **63.125 s** and the total from 67.5 to **67.125 s**. The VO "The guns: Jerusalem," must fit in 1.417 s, or run over the map.
6. **Cuts 7 and 8:** C31 and C32 (refused, never retried) become the v3 start frames `colour-test/v3/C31-v3.png` and `C32-v3.png` as greyscale stills with an ffmpeg zoompan push (1.00 to 1.06), pillarboxed 4:3. Nothing is AI-animated. **FLAG:** these are stills under the "no pictures" rule (an owner-approved exception for this cut).
7. **Cuts 30 and 31:** A1 and B1 are `clips/A1-seedance-comp.mp4` (3.0 s) and `clips/B1-seedance-comp.mp4` (2.17 s), the composites the owner approved on 7 Nov (LOG.md "A1 and B1 composites"), from 0.0.

Applied from CLIP-QA-0811.md, where its usable range is shorter than the cut list's range or names a different range:
8. **Cut 3, C2:** src 2.208-3.0 (QA "best 2.2-3.0"), not 0-0.8.
9. **Cut 4, C4:** src 0.208-2.0 (QA 0.2-2.0), not 0-1.8. This avoids the model-made background faces from about 3 s.
10. **Cut 12, C8:** the QA range is 0-2.6, and the cut needs 3.4. I used src 0-2.583 (62 frames) **slowed to 0.756x** (the QA's first option, "slow to about 76 %"), so all VO sync is kept. This avoids the smear and dissolving figure from 3.2 s. The duplicate frame at about 0.54 s is still in.
11. **Cut 13, C10:** cropped to the top 76 % of the frame (centred, then scaled to fill), as the QA asks ("crop the bottom band"). In the sampled frames the hands and the white card are out of the picture.
12. **Cut 15, C13:** an edit push of 1.00 to 1.08 over the 0.6 s, as the QA recommends, because the clip is near still.
13. **Cut 17, C16:** src 2.417-3.708 (QA "about 2.4-3.7", where she raises the Sten), not 0-1.3.
14. **Cut 18, C17:** src 0.208-1.625 (QA 0.2-1.6), not 0-1.4.
15. **Cut 25, C22:** the QA says C22 is usable only to 3.3 s (tear or sweat beads after that; this is the open item in EDIT-FIX.md). Cut 25 is now **src 2.917-3.292, only 9 frames (0.375 s)**, not 2.917-3.917 (1.0 s). The 0.625 s it loses goes to the **black cut 26 (3.4 to 4.025 s)**, so cut 27 still starts at 49.0 s and no later sync moves. The hard cut to black comes 0.625 s earlier (44.958 s), and "We do not wait." (about 46.0 s) is still on black. The QA's other option, a 1.0 s reuse from 2.2-3.2, would overlap cut 23 (0-2.917), so I did not use it.
16. **Cut 33, C26:** src 1.833-4.042, the QA's "1.8-4.0 accepting the last stutter frames" option, which gives the full 2.2 s. The other QA ranges (0-1.4, 2.1-4.0) are shorter than 2.2 s.
17. **Cut 27, C23:** 2 px were cut from the top and bottom, which have edge lines. src 0-3.583: the QA gives "0.0-3.0 or 1.0-4.0" as 3.0 s windows and no defect inside 0-4.0, so I read 0-3.6 as inside its usable range.

Not applied, though the QA range is shorter:
18. **Cut 2, C1:** the QA marks only 0.0-0.4 s as clean, because the man in glasses gets a model-made, but stable, face from about 0.5 s on. The QA calls it an owner call ("if the owner accepts invented faces ... it is a KEEP"). Cutting the opening shot to 0.4 s would break the opening card at 2.0 s and the first VO line, so I kept 0-3.417. **FLAG: owner call.** The made-up face is visible on the contact sheet (cut 2).

Placeholders (no source in the folder; nothing downloaded):
19. **Cuts 6, 9, 10 (real film: Vienna 1938 Nitsche, Westerbork 1944 06.08 and 07.57):** no copy of either film is in the film folder (searched by name). They are black with a grey label saying what goes there. Durations are as the cut list gives them.
20. **Cut 35 (map):** no game map capture exists in the folder. The only map image is `stills2/Smap-take1.png`, which is an AI still, not the game. The cut is a black card labelled "MAP", 4.0 s.

Rounding: cut 1 is 38 frames (1.583 s), so cut 2 starts at 1.583 s, not 1.6 s. Other starts are within half a frame of nominal (see the table).

## Flags (look at these)

- **F1, cut 24:** a still hold on C20b frame 96, which breaks "no pictures". It needs a C20b re-plan or a new shot. Its frame also shows the grey-haired man's pale, glove-like hands (the LOG.md flag on C20b from about 1.5 s); they are visible at the left of the hold.
- **F2, cuts 7 and 8:** stills with a push (owner-approved fallback, but still pictures).
- **F3, cuts 6, 9, 10, 35:** placeholders. About 9.2 s of the film is placeholder black (2.167 + 1.208 + 1.792 + 4.0).
- **F4, cut 2 (C1):** a model-made face from about 0.5 s (QA owner call).
- **F5, cuts 30 and 31 (A1, B1):** the comp files are **black and white**. DIRECTOR-REVIEW-colour-v2 asks for "A1, approved, with colour transferred". No colour version of A1 or B1 is in `clips/`, so between C23 (B&W, intended) and C25 (colour) the film runs B&W, then colour.
- **F6, cut 25:** only 9 frames now (see deviation 15). The snap is cut short before the end of its push. Check at full speed whether 0.375 s reads as a snap or as a flash frame.
- **F7, cut 12 (C8):** 0.756x slow-motion on surf, and one duplicate source frame at about 0.54 s. Check at speed for judder.
- **F8, cut 23 (C22):** 0.814x, as the owner ruled.
- **F9, cut 21 (C20b):** the portrait's head leaves frame at about 35.2 s (see deviation 3).
- **F10, pillarboxed portrait and square clips** (cuts 17, 18, 20) have wide black side bars. This follows the "no re-crop" ruling, but in a 16:9 film they read as letterbox.
- **F11, cut 19 (C15 retake):** the LOG flags that its motion is handheld shake and small weight shifts, so check at full speed that it does not read as a still.
- **F12:** no audio. I did not lay a sound bed (allowed, not required). Cards and lower thirds are in a temp style, not designed.

## What I saw on the contact sheet

I checked the sheet and a strip of extra frames (frames 47/48, 278/316, 600, 1027/1069, 1070/1078/1079):
- The cut-2 lower third appears at frame 48 (2.000 s), as the cut list asks.
- In cut 14 the flash shows at frame 600 (25.0 s), and the white right edge is gone after the 20 px crop. In the first build it showed as a white line at the right edge of the pillarboxed picture.
- Cuts 7 and 8: the push moves (frames 278 and 316 differ), they are greyscale, and both are pillarboxed 4:3.
- Cut 24: the hold is on the bearded man, the man in the grey suit and the grey-haired man. The wall portrait is out of frame.
- Cut 25 ends on BG's eyes, before the tear beads (frame 1078). Cut 26 is black from frame 1079.
- Cut 2 (C1): the man in glasses is turned toward the camera with a made-up face (F4).
- Cuts 30 and 31 are B&W (F5).
- Cut 33 (C26) and cut 34 (C28): the bus and the gun hold; no shield writing is visible at sheet size.
- Not checked: playback at full speed (judder, the C26 stutter frames, the C8 duplicate frame).
