# Stage 1 — corrected P0 handoff

## Strict UI constraint

**Only checkbox rows. No chips, tags, clouds or pill controls.**

Reference interaction: Doximity preferred-source list + ya.ru bank filter: search field, vertical rows, checkbox on the right, explicit Continue/Apply action.

## Lev rule: population is NOT Step 1

Step 1 answers only **«какая у вас специальность / профессиональный домен?»**.

Do not add `Детская / Взрослая` as a first-screen dimension and do not create an `adult vs pediatric` refinement after Cardiology, Endocrinology, Oncology etc. Patient population belongs to Step 4.

Therefore:
- `Кардиология` is a checkbox;
- `Детская кардиология` is not a separate Step-1 checkbox;
- exact search `детский кардиолог` redirects to `Кардиология` and the UI says that patient age is configured later;
- `Педиатрия` remains a specialty because it is already an explicit professional specialty in the product list, not a generated `child/adult` modifier;
- raw 435н master keeps pediatric canonical records for regulatory/verification use, but P0 personalization UI does not expose them as a separate age choice.

## Discoverability of true sub-specialties

True domain/procedural distinctions can remain nested checkbox rows under the top-level specialty. Current P0 examples: neurosurgery, cardiovascular surgery, thoracic surgery, plastic surgery, maxillofacial surgery, coloproctology, radiotherapy, etc.

## State

`selected specialtyIds[]` is a set. No selected chips are rendered. Selection is visible only via the checkboxes and a count in the footer.

## Search

Search returns checkbox rows. It never opens a second selector and never renders a chip. Child/adult aliases are redirects to the parent professional domain.