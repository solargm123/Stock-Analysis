# Bug Triage Workflow

For symptoms such as "กดไม่ได้", "refresh ไม่ได้", blank data, wrong value, or unknown errors.

## Classify first
UI -> State -> Auth -> API/Edge Function -> Database -> Accounting/Calculation

## Workflow
1. Reproduce the exact symptom from existing evidence.
2. Search for the exact control, handler, function, endpoint, or error string.
3. Inspect only that layer and its direct dependency.
4. Find root cause before patching.
5. Apply the smallest fix.
6. Test the failed flow once, then one adjacent flow.
7. Stop expanding scope when evidence no longer points outward.

Never rescan the whole repo just because the initial cause is unknown.
