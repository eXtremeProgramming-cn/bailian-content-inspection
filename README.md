# bailian-content-inspection

An independent, documentation-grounded page explaining how **content inspection** works on Alibaba Cloud Model Studio (DashScope / 百炼): the `X-DashScope-DataInspection` request header, the values it accepts, what each value means, and how to read the `DataInspectionFailed` error.

**Why this page exists.** Agent-style workloads (long prompts, retrieved documents, research material) occasionally trip the platform's content inspection on legitimate input, and the official error reference's remedy ("modify the input and retry") does not fit that case. This page reads the official documentation closely — including where it is incomplete — so that developers and the AI agents they work with can understand the mechanism and configure it knowingly.

**Editorial rules** (enforced in review, see git history):

1. Every factual claim links to an official Alibaba Cloud page; sources and access dates are listed at the bottom of the page.
2. Where official documentation is incomplete or silent (e.g. the `disable` value does not appear in the text-API reference, only in realtime-speech example code), that status is stated plainly instead of being smoothed over.
3. The page presents the full configuration surface — including the AI Guardrail value-added service, the whitelisting (内容加白) ticket process, and the boundary that model-layer compliance behavior is unaffected — so it reads as what it is: an explanation of how the feature works, not a workaround note.

## Publish

GitHub Pages from the main branch root (`index.html`, no build step):

```bash
gh repo create extremeprogramming-cn/bailian-content-inspection --public --source=. --push
# then: repo Settings → Pages → Source: Deploy from a branch → main / (root)
```

Site URL: `https://extremeprogramming-cn.github.io/bailian-content-inspection/`

## Verification log

- 2026-09-20 — initial version. Full text fetched and checked for: text-API reference (values), content-security page (guardrail wiring, billing, whitelisting), error-code page (error family wording), realtime-speech guide (official `disable` example). Gateway behavior on both mainland endpoints (OpenAI- and Anthropic-compatible) verified empirically: the header is accepted, unknown headers are ignored.
