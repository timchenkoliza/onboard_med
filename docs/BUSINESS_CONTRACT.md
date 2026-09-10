# P0 Business Contract — Doctor Profile Popup

**FROZEN correction: 10.09.2026**  
**Target release: 14.09.2026**

## UI invariant

Step 1 uses **vertical checkbox rows only**. No chips, tags, clouds or pill controls.

Reference interaction: Doximity preferred-source settings + ya.ru bank filter: search field, scrollable rows, checkbox state, explicit CTA.

## Step 1 — specialty

- multi-select;
- 15 main specialties are shown as checkbox rows;
- search works over the same checkbox-list pattern;
- true narrow specialties may be shown as indented checkbox rows;
- explicit `Детская / Взрослая` variants are **not** a separate Step-1 dimension;
- age/patient population belongs to Step 4;
- queries such as `детский кардиолог` map to the base professional domain instead of rendering a separate pediatric checkbox;
- `Далее` is enabled only after at least one selection;
- no auto-advance;
- IDs are deduplicated.

The P0 onboarding profile is a personalization profile, not a legal assertion of verified qualification. Regulatory canonical records remain in the source dataset for a separate verification flow.

## Step 2 — experience
Single-choice.

## Step 3 — workplace
Multi-select checkbox rows; `not_practicing` is mutually exclusive with all workplaces.

## Step 4 — patient groups
This step owns population context: adults, children/adolescents, pregnant/lactating, older patients. Do not duplicate this dimension on Step 1.

## Step 5 — preferred sources
Doximity-like preference flow within the same implementation constraint: searchable vertical source rows + checkboxes. Preference is a ranking boost, not an allowlist.

## Submit
One atomic save after Step 5; success only after backend confirmation.