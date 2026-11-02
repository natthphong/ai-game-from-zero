# AI Video Skills ที่เลือกใช้

**ต้นทาง:** https://github.com/zhuyansen/awesome-claude-video-skills

Repository นี้เป็น catalog ของ video-production skills ไม่ใช่ชุดสร้างเกมหรือสิ่งที่ต้อง clone ทั้งหมด

## แนะนำใช้จริง
1. [Remotion Official Skills](https://github.com/remotion-dev/skills) — ทำ Motion Graphic ซ้อนบนคลิป เช่น Chapter Intro, prompt cards, zoom/highlight, tutorial steps, before/after, outro
2. [FFmpeg](https://ffmpeg.org/) — ตัด คลิปจริง สร้าง proxy/รวมเสียงและภาพ หรือใช้ NLE ที่ถนัด
3. [OpenRouter TTS](https://openrouter.ai/docs/guides/overview/multimodal/tts) — อ่านบทพากย์ภาษาไทย (เลือกรุ่น/เสียงจากรายการที่ใช้งานได้ในเวลาผลิต) แบ่งบล็อกเพื่อปรับได้สะดวก

## ไม่จำเป็นต้องใช้
- HyperFrames / OpenMontage / explainroo / onetake ทั้งหมดพร้อมกัน — เพิ่มความซับซ้อนโดยไม่ช่วยเรื่องการสอนเกม
- AI generated cinematic เป็นภาพหลัก — เพราะเป้าคือพิสูจน์ว่าทำเกมได้จริง

## Workflow
1. เก็บ recording หน้าจอ + gameplay จริงในแต่ละ milestone
2. ตัด A-roll จากเสียงพากย์และ screen recording
3. ทำ graphic cards แยกด้วย Remotion สำหรับ prompt, step, error/fix
4. ตรวจการออกเสียง OpenRouter TTS, ปรับแบ่งช่วงแล้ว export
5. ประกอบในโปรแกรมตัดต่อ ตรวจ gameplay ไม่ถูกตัดจนทำให้คนดูทำตามไม่ได้

## แนวทางซื่อสัตย์กับคนดู
เขียนผลที่เกิดขึ้นหลังทดสอบจริงเท่านั้น ไม่สร้างภาพ gameplay ปลอมอ้างว่าเป็นเกมที่เล่นได้
