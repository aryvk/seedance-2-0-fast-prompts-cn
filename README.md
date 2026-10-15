# Seedance 2.0 Fast Prompts — 8 Tested Recipes With Outputs

<!-- conv-kit:v1 -->

<p align="center">
  <img src="assets/badges/price.svg" alt="observed unit price"> <img src="assets/badges/billing.svg" alt="billing model"> <img src="assets/badges/compat.svg" alt="OpenAI-compatible endpoint">
</p>

<p align="center">
  <img src="assets/01-product-ad-ceramic-mug-thumb.jpg" width="820" alt="Sample video frame generated through APIMart">
</p>

> **from $0.0213 per second** on the APIMart route (billed by resolution tier) — 一个 OpenAI 兼容端点 `https://api.apimart.ai/v1`，无需包月套餐。*(数据观测于 2026-10-12)*

**[Get an API key](https://go.apimart.ai/k-004e2a)** · **[Live pricing](https://go.apimart.ai/k-c23bc5)** · **[Model page](https://go.apimart.ai/k-f76c06)** · [⚡ 60-second quickstart](#quickstart)

**为什么团队通过 APIMart 调用 Seedance 2.0 Fast（`doubao-seedance-2.0-fast`）**

- **一个 Key，整个目录。**同一个 `https://api.apimart.ai/v1` base URL 和 `Authorization` 请求头即可访问 Seedance 2.0 Fast（`doubao-seedance-2.0-fast`）以及图像、视频、语言等 300+ 模型——只需切换 `model` 字段，客户端无需改动。
- **$1 起充，按量付费。**没有订阅、也没有需要预先估算用量的预付费套餐：最低充值 $1，调用多少扣多少。
- **费用随响应一并返回。**每个完成的任务都会报告实际计费金额（`cost` / `credits_cost`）；状态为 `failed` 的任务会自动退款。
- **原生异步设计。**提交任务、拿到 `task_id`、轮询 `GET /v1/tasks/{id}`——批处理和重试都是普通的队列工作，不需要定制集成。

<!-- /conv-kit:v1 -->

**中文环境也叫:** 即梦视频

Four **Seedance 2.0 Fast prompts** listed with an example render, the duration, and what the call costs on this route. Copy a recipe, keep the structure, swap the subject.

- Model: `doubao-seedance-2.0-fast`
- Recipes: **4** (machine-readable in [`data/prompts.json`](data/prompts.json), table in [`PROMPTS.md`](PROMPTS.md))
- Effective price used below: **$0.0213 per second** — estimated cost of the whole set: **$0.0852**

## What separates a usable recipe from a wasted call

Three rules held up across every render in this set:

1. **Name the material, not the adjective.** "Frosted glass", "matte ceramic", "layered paper" steer rendering far more
   than "beautiful" or "high quality".
2. **Set the light explicitly.** "Single softbox from the left", "golden hour backlight", "focus-stacked studio light"
   remove the guesswork the model would otherwise do for you.
3. **Pin the framing.** Ratio plus lens language (`85mm`, `24mm`, `macro`, overhead flat lay) decides whether the output
   drops into a layout unchanged.

## Prompt structure cheat-sheet

| Slot | What to write | Example |
| --- | --- | --- |
| Subject | one concrete object or person, with material | *frosted glass perfume bottle* |
| Light | direction + quality | *single softbox from the left* |
| Framing | ratio + lens or distance | *3:4, medium format look* |
| Setting | surface, backdrop, environment | *wet black stone slab* |
| Finish | render or film character | *commercial product photography* |

## The gallery

Each row is one recipe: example render, category, duration, cost on this route and the exact prompt.

| Output | Recipe | Duration | Cost | Prompt |
| --- | --- | --- | --- | --- |
| <img src="assets/01-product-ad-ceramic-mug-thumb.jpg" width="220" alt="Sample video frame generated through APIMart"> | Product ad | 5s | $0.0213 | `Slow 180° orbit around a matte ceramic mug on a dark stone plinth, steam rising, soft key light from camera left, shallow depth of field, product commercial` |
| <img src="assets/02-cinematic-rainy-street-thumb.jpg" width="220" alt="Sample video frame generated through APIMart"> | Cinematic | 5s | $0.0213 | `Rain soaked street at night, camera pushes in slowly past neon reflections, a lone figure with an umbrella walks away from camera, 35mm anamorphic, film grain` |
| <img src="assets/03-food-ad-steam-thumb.jpg" width="220" alt="Sample video frame generated through APIMart"> | Food commercial | 5s | $0.0213 | `Overhead view tilting down to 45° onto a steaming bowl of ramen, chopsticks lift the noodles, warm practical light, macro detail, appetising commercial grade` |
| <img src="assets/04-architecture-flythrough-thumb.jpg" width="220" alt="Sample video frame generated through APIMart"> | Architecture | 5s | $0.0213 | `Slow aerial flythrough of a concrete villa at dusk, camera pushes across the infinity pool toward warm interior light, 24mm, ultra sharp` |

## Run a recipe yourself

```bash
export APIMART_API_KEY=...
python examples/run_recipes.py --dry-run                 # list the recipes, no network
python examples/run_recipes.py --limit 2                 # generate two of them
```

```bash
curl --request POST --url https://api.apimart.ai/v1/videos/generations \
  --header "Authorization: Bearer $APIMART_API_KEY" --header 'Content-Type: application/json' \
  -d '{"model":"doubao-seedance-2.0-fast","prompt":"<paste a prompt>","duration":5,"resolution":"720P","size":"16:9"}'
```

Result links expire 72 hours after completion, so store the outputs; the completed task carries `cost` for reconciliation.

## FAQ

**Are these prompts free to reuse?**

Yes — the prompt text in this repository is MIT licensed. The generated images and any third-party marks they contain remain your responsibility, and you should check the model vendor's terms before publishing commercial work.

**Why do the recipes use different aspect ratios?**

Because ratio is a layout decision, not a style one: 1:1 for catalogue and icons, 16:9 for hero and video thumbnails, 3:4 or 2:3 for portraits and print. Pinning it up front avoids cropping later.

**How much does one recipe cost to run?**

**from $0.0213 per second** on the APIMart route (billed by resolution tier). Every completed task reports the exact amount in its `cost` field; a failed task is refunded.

**Can I use a recipe as a template for another subject?**

That is the point. Keep the structure (subject + light + framing + setting + finish) and replace the subject; changing everything at once makes it impossible to tell which phrase moved the output.

## Attributed links (how this repository is measured)

| Purpose | Attributed link | Target |
| --- | --- | --- |
| Model page | <https://go.apimart.ai/k-f76c06> | `apimart.ai/zh/model/doubao-seedance-2-0-fast` |
| Live pricing | <https://go.apimart.ai/k-c23bc5> | `apimart.ai/zh/pricing` |
| Get an API key | <https://go.apimart.ai/k-004e2a> | `apimart.ai/zh/keys` |

Outbound APIMart links are minted through the promo link API; hand-made tracking parameters are rejected by
`tools/check_links.py` in CI.

## Disclosure

Seedance 2.0 Fast is a third-party model served through APIMart. This repository publishes prompts, example renders and
cost logic; it does not claim official status for any vendor, and model names and documentation belong to their owners.

## Repository map

```text
README.md              gallery, prompt structure and FAQ
PROMPTS.md             every recipe in one table
data/prompts.json      machine-readable recipes with per-unit cost
examples/run_recipes.py  batch runner (dry-run safe for CI)
tools/check_links.py   attribution guard
assets/                example renders via the APIMart image API (JPEG)
```

## License

MIT — see [LICENSE](LICENSE).
