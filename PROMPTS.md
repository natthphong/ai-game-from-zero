# Prompts — สร้างเกม RPG ตัวละครเดิน 8 ทิศ เปลี่ยนชุดได้

คัดลอกทีละขั้นไปวางใน **Codex** หรือ **Claude Code** ที่เปิดโฟลเดอร์เกมอยู่ · **เปิดเกมเช็คก่อนไปขั้นถัดไปทุกครั้ง**
prompt ภาพ (ขั้น 3–7) ใช้ใน Codex หรือ ChatGPT ได้ · ภาพชุดละ ~2–5 นาที

---

## ขั้น 0 — ตรวจเครื่อง

```text
คุณคือครูสอนทำเกมสำหรับคนไม่เคยเขียนโค้ด ตรวจโฟลเดอร์นี้และเครื่องมือที่มีอยู่ก่อน ห้ามลบไฟล์หรือเขียนทับงานเดิมโดยไม่บอก ตรวจ Node.js, npm, Git และไฟล์เดิม ถ้าไม่มีเกมอยู่ให้เสนอวิธีสร้างใหม่ด้วย Phaser 3 + Vite + TypeScript อธิบายขั้นตอนภาษาไทยสั้น ๆ และบอกคำสั่งที่ฉันต้องรัน อย่าติดตั้งแพ็กเกจที่ไม่จำเป็น
```

## ขั้น 1 — วางแผนให้เล็ก

```text
ช่วยออกแบบเกม Fantasy RPG แบบ 2D มุมมองจากด้านบน เล่นในเบราว์เซอร์ เป็น prototype เล็ก ๆ ที่ผู้เริ่มต้นทำตามได้ ต้องมี: เดิน 8 ทิศด้วยปุ่มลูกศร/WASD, แผนที่เดียว, ศัตรูหนึ่งชนิด, โจมตีและ HP, ตัวละครเปลี่ยนชุดได้, แพ้แล้วเริ่มใหม่ได้ ห้ามเพิ่มระบบ server, login, payment หรือ multiplayer ในเวอร์ชันแรก สร้าง GAME_PLAN.md ที่มี controls, milestone ทีละขั้น, เกณฑ์ที่เปิดเกมแล้วเช็คได้ และสิ่งที่ยังไม่ทำ ก่อนแก้โค้ดให้สรุปแผนให้ฉันทราบ
```

## ขั้น 2 — เดินได้ก่อน

```text
ทำเฉพาะ milestone แรกตาม GAME_PLAN.md ด้วย Phaser 3 + Vite + TypeScript ให้ npm install และ npm run dev แล้วเล่นในเบราว์เซอร์ได้ ตัวละครเป็นกล่องสีฟ้าไปก่อน เดินด้วยลูกศร/WASD ได้ 8 ทิศ ชนขอบแผนที่แล้วหยุด อย่าเพิ่มศัตรูหรือระบบอื่น บอก URL ที่ต้องเปิดและวิธีทดสอบด้วยตัวเอง
```
ผ่านเมื่อ: กดลูกศรแล้วเดิน ปล่อยแล้วหยุด ชนขอบแล้วหยุด

## ขั้น 3 — ตัวเปล่าสีเนื้อ (ภาพ)

```text
Cute 2D fantasy RPG game character, front view facing the viewer, full body, standing straight in a neutral A-pose with arms slightly away from the body and feet apart, centered. A young adventurer BASE BODY for a dress-up system: warm tan skin tone body, short dark brown hair, friendly face, barefoot, wearing ONLY a plain simple light-grey fitted sleeveless undershirt and plain light-grey shorts (modest base layer, nothing else, no accessories, no weapon). Solid flat pure magenta (#FF00FF) background filling the whole canvas, no gradient, no floor, no shadow. No text.
```
ทำไมพื้นชมพูม่วง: เป็นสีที่ไม่มีในตัวละคร ตัดพื้นทิ้งได้เป๊ะ · ทำไมกางแขน: ใส่เสื้อแขนยาวทีหลังจะไม่เละ
> ทริก: ถ้าชุดมีเกราะสีเงิน ให้ตัวเปล่าใส่สีอื่นที่ไม่ชน (ไม่งั้นตัดชุดแล้วอกเป็นรู)

## ขั้น 4 — ใส่ชุด (แนบรูปตัวเปล่าไปด้วยทุกครั้ง)

```text
EDIT the attached image. It is the BASE BODY of a game character on a magenta background. Keep the canvas, the character's exact height, head size, face, hair, skin, arms, hands, legs, feet, pose and position 100% unchanged, pixel for pixel. Only paint clothing on top of the body, following its exact outline. Keep the same cartoon line style and the same flat magenta background.
Outfit: blue knight tunic over silver chest plate, silver shoulder pads, brown belt, silver gauntlets, steel boots. No helmet, no weapon.
```
ชุดอื่น: เปลี่ยนแค่บรรทัด `Outfit:` เช่น
- `long deep purple wizard robe with gold trim, wide purple pointed wizard hat, brown sash, purple shoes. No staff.`
- `forest green hooded cloak with the hood DOWN, brown leather vest, green trousers, brown leather boots and bracers. No bow.`

ผ่านเมื่อ: เอาภาพชุดวางซ้อนตัวเปล่าแล้วหัวกับเท้าอยู่ที่เดิม · ไม่แนบตัวเปล่า = AI วาดคนใหม่

## ขั้น 5 — ท่าเดิน 8 ทิศ (แนบ 2 รูป: ภาพนำท่าเดินจาก `guides/` + ตัวเปล่าจากขั้น 3)

ทำ 5 ทิศ: `walk_front` `walk_front34` `walk_side` `walk_back34` `walk_back` · อีก 3 ทิศฝั่งซ้ายให้เกมกลับด้านภาพ
**อย่าสั่งรูปเดียว 64 ท่า** — ช่องเล็กเกิน ขาไม่สลับ และหันผิดทิศ

```text
Two images are attached. IMAGE 1 is a rough clay BLOCKOUT of a walk animation (8 frames, 2 rows of 4). IMAGE 2 is the CHARACTER (the base body).
REPAINT IMAGE 1 into a finished 2D game SPRITE SHEET of the boy from IMAGE 2, [VIEW], walking.
Keep image 1 exactly: the same 8 figures in 2 rows of 4, at the same places and sizes, every arm, leg and foot exactly where the blockout's is. In frames 1-4 the near leg steps forward; in frames 5-8 the far leg is forward and the near leg is back. Never draw the same leg forward in all frames. The arms swing opposite to the legs.
The boy is identical in all 8 frames, same face, hair, skin and clothes as image 2. Only the arms and legs move. Keep the chibi head size of image 1.
Clean anime game sprite art, crisp dark outline, soft cel shading. Plain flat solid magenta (#ff00ff) background everywhere, no shadow, no floor, no grid lines, no frame numbers, no text.
```
`[VIEW]` ต่อทิศ: `seen from the FRONT, facing the viewer` · `in THREE-QUARTER FRONT view, turned toward the lower right` · `seen from the RIGHT SIDE, facing right` · `in THREE-QUARTER BACK view, walking away toward the upper right` · `seen from the BACK, walking away from the viewer`

## ขั้น 6 — ใส่ชุดบนแผ่นท่าเดิน (แนบ 2 รูป: แผ่นท่าเดินตัวเปล่าทิศนั้น + รูปชุดจากขั้น 4)

```text
Two images are attached. IMAGE 1 is a finished walk-animation sprite sheet (8 frames, 2 rows of 4) of a chibi boy BASE BODY in a grey undershirt and shorts on a magenta background. IMAGE 2 shows the SAME boy wearing an outfit.
EDIT IMAGE 1 and keep its VIEW and walking direction (if image 1 shows the boy from behind, the result must also show his back, never his face): dress the boy in every one of the 8 frames in the outfit from IMAGE 2: [OUTFIT]
Keep everything else in image 1 exactly as it is: the same 8 figures at the same places and sizes, the same face, hair, head size, skin, the exact pose of every arm, leg and foot in every frame. Only paint the clothes on top of the body, following each frame's pose. Keep the plain flat solid magenta (#ff00ff) background, no shadow, no text.
```
> ถ้าขาเปล่าโผล่หลังเกราะบางเฟรม: ให้ชั้นชุดเก็บทั้งตัว (บังตัวเปล่าหมด) แทนการตัดเฉพาะเสื้อผ้า

## ขั้น 7 — อาวุธ (ภาพเดียว 3 ชิ้น)

```text
Three separate game weapon sprites in the same chibi anime sprite style, side by side with lots of empty space between them, each standing VERTICAL with its grip at the bottom and the tip at the top: 1) a short steel knight sword with a blue and gold hilt, 2) a wooden mage staff with a glowing purple crystal at the top, 3) a wooden ranger bow drawn upright with no arrow. Crisp dark outline, soft cel shading. Plain flat solid magenta (#ff00ff) background, no shadow, no hands, no text.
```

## ขั้น 8 — โค้ดซ้อน 3 ชั้น (วางใน Codex / Claude Code)

```text
เอาภาพในโฟลเดอร์ art/ มาทำตัวละคร: ตัดพื้นสีชมพูม่วง (#ff00ff) ออกให้โปร่งใส แผ่นท่าเดินแบ่งเป็น 8 เฟรม (2 แถว 4 ช่อง)
ตัวละครมี 3 ชั้นซ้อนกัน ตัวเปล่า ชุด อาวุธ ทุกชั้นใช้ทิศและเฟรมเดียวกัน จุดยึดที่เท้าเดียวกัน
มี 5 ทิศจากภาพ (หน้า เฉียงหน้า ข้าง เฉียงหลัง หลัง) เดินทางซ้ายให้กลับด้านภาพทั้ง 3 ชั้นพร้อมกัน
กด C เปลี่ยนชุด กด Q เปลี่ยนอาวุธ อาวุธวางที่มือของแต่ละเฟรม หันหลังให้อาวุธอยู่หลังตัว ตรวจ build แล้วบอกวิธีทดสอบ
```
ผ่านเมื่อ: กดลูกศรสองปุ่มพร้อมกันแล้วหันทแยง · ขาสลับซ้ายขวา · เดินซ้าย = เดินขวากลับด้าน · C / Q เปลี่ยนได้

## ขั้น 9 — หา asset ฟรี

```text
Asset sources:
• https://quaternius.com/
• https://kenney.nl/assets
• https://kaylousberg.itch.io/
• https://itch.io/game-assets/free
• https://opengameart.org/
• https://polyhaven.com/
• https://ambientcg.com/
• https://www.mixamo.com/

Requirements:
1. Analyze the game's art direction and identify required assets.
2. Search for matching asset packs from these sources.
3. Prioritize CC0 assets and compatible art styles.
4. Verify the license and whether commercial use is permitted.
5. Download assets where direct download is available and permitted. Otherwise provide download links.
```
ในคลิปใช้ Kenney Foliage Pack (CC0) แทนต้นไม้ที่วาดด้วยโค้ด · บอก AI ให้เรียงความลึกตามแกน y ตัวละครจะเดินลอดหลังต้นไม้ได้

## ขั้น 10 — ศัตรู + ลองเล่นให้แพ้

```text
เพิ่มมอนสเตอร์เพียงหนึ่งประเภท เดินเข้าหาผู้เล่นในระยะใกล้ กด Space เพื่อโจมตี มี HP ทั้งผู้เล่นและมอนสเตอร์ โจมตีโดนครั้งละ 25 มอนสเตอร์มี HP 100 โดนชนแล้วให้ผู้เล่นอมตะ 1 วินาที มอนสเตอร์ตายแล้วเกิดใหม่ภายหลัง แพ้แล้วกด Enter เริ่มใหม่ เลือดกลับมาเต็ม ตรวจ build แล้วอธิบายวิธีทดสอบ
```
ผ่านเมื่อ: ยืนเฉยๆ ให้ชนจนแพ้ ขึ้นหน้าแพ้ กด Enter แล้วเลือดเต็ม

## Prompt แก้บั๊ก — ใช้ซ้ำได้ทุกขั้น

```text
เกมมีปัญหานี้: ฉันกด [อะไร] คิดว่าจะ [เกิดอะไร] แต่ที่เกิดจริงคือ [อะไร]
ตรวจ root cause จากโค้ดและ logs ก่อน อธิบายเป็นภาษาไทยแบบง่าย แล้วแก้ไขด้วยการเปลี่ยนแปลงที่เล็กที่สุด ห้ามลบฟีเจอร์เดิมเพียงเพื่อให้ error หาย สรุปว่าทำอะไรและให้ฉันทดสอบตรงไหน
```
