# Manara | منارة

**منارة** — رفيق دعم نفسي للشباب في ليبيا، بلهجة قريبة منهم، وبخصوصية كاملة.
**Manara** — A personal emotional-support companion for young people in Libya.

## المشكلة | The problem
الوصول إلى الدعم النفسي في ليبيا صعب، والوصمة الاجتماعية تمنع كثيراً من الشباب من طلب المساعدة.
Mental health support is hard to reach in Libya, and stigma stops many young people from asking for help.

## كيف يعمل | How it works
- **محادثة داعمة** تستمع وتتعاطف، دون تشخيص طبي. / Supportive chat in a Libyan-friendly Arabic dialect, no medical diagnosis.
- **تتبّع المزاج والمواضيع** لاكتشاف الأنماط (مثل ضغط الامتحانات). / Mood and topic tracking to spot patterns.
- **ربط بدليل محلي موثّق** (مختصون، خطوط ساخنة، دعم جامعي). / Matching to a verified local directory.
- **تصعيد من ثلاث مستويات | Three-level escalation:**
  1. دعم عادي / Normal support
  2. اقتراح التواصل مع رسالة جاهزة / Suggested contact with a ready-made message
  3. شاشة طوارئ ثابتة بأرقام الطوارئ وزر "شخص موثوق" / Urgent fixed screen with emergency numbers and a "trusted person" button

## التقنية | Tech
Flutter · encrypted local storage · LLM API (chat & classification) · embeddings + RAG for resource matching · fixed rule-based risk detection.

## الخصوصية | Privacy by design
- لا حاجة لحساب / No account needed
- البيانات تبقى على الجهاز / Data stays on the device
- تُخفى البيانات الشخصية قبل وصولها للنموذج / Personal details are masked before reaching the model
- لا يُرسل شيء لأي جهة دون موافقة المستخدم / Nothing is shared without the user's consent

## الخطوة التالية | Next step
كتابة الـ system prompt ومخطط المخرجات، ثم اختبار النماذج على 10 أمثلة بلهجة ليبية.
Write the system prompt and output schema, then test models on 10 Libyan-dialect examples.

> ⚠️ منارة أداة دعم وتوجيه وليست بديلاً عن الرعاية الطبية. في الطوارئ تواصل مع الجهات المختصة فوراً.
> Manara is a guidance tool, not a substitute for professional care.
