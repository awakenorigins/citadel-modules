# 🏰 CITADEL MODULES HUB

Mục lục toàn bộ module của **SUPERCITADEL** — Vietnamese business OS. Mỗi module có repo mirror riêng; source of truth là monorepo [supercitadellab](https://github.com/NachaFromMars/supercitadellab).

> Sync gần nhất: 2026.07.10 · Tự động bằng `scripts/sync-modules-hub.sh` trong monorepo.

## Danh sách module

| Module | Path monorepo | Ghi chú |
|---|---|---|
| [accounting](https://github.com/NachaFromMars/citadel-module-accounting) | `modules/accounting` | 1 migrations |
| [chat](https://github.com/NachaFromMars/citadel-module-chat) | `modules/chat` | 2 migrations |
| [crm](https://github.com/NachaFromMars/citadel-module-crm) | `modules/crm` | 1 migrations |
| [hr](https://github.com/NachaFromMars/citadel-module-hr) | `modules/hr` | 2 migrations |
| [inventory](https://github.com/NachaFromMars/citadel-module-inventory) | `modules/inventory` | 1 migrations |
| [ke-toan-10a](https://github.com/NachaFromMars/citadel-module-ke-toan-10a) | `modules/ke-toan-10a` | 1 migrations |
| [notification](https://github.com/NachaFromMars/citadel-module-notification) | `modules/notification` | 1 migrations |
| [om](https://github.com/NachaFromMars/citadel-module-om) | `modules/om` | 1 migrations |
| [soul-inventory](https://github.com/NachaFromMars/citadel-module-soul-inventory) | `modules/soul-inventory` | 7 migrations |
| [soul-manager](https://github.com/NachaFromMars/citadel-module-soul-manager) | `modules/soul-manager` | 3 migrations |
| [soul-restaurant](https://github.com/NachaFromMars/citadel-module-soul-restaurant) | `modules/soul-restaurant` | 4 migrations |
| [soul-sale](https://github.com/NachaFromMars/citadel-module-soul-sale) | `modules/soul-sale` | 3 migrations |
| [soul-trade](https://github.com/NachaFromMars/citadel-module-soul-trade) | `modules/soul-trade` | 8 migrations |
| [soul-wallet](https://github.com/NachaFromMars/citadel-module-soul-wallet) | `modules/soul-wallet` | 2 migrations |

## Forge module mới
1. Đọc [docs/MODULE-FORGE-GUIDE.md](docs/MODULE-FORGE-GUIDE.md) — stack, manifest v2, contract, quy tắc.
2. Đọc [docs/ADD-MODULE-PLAYBOOK.md](docs/ADD-MODULE-PLAYBOOK.md) — quy trình nạp vào Citadel.
3. Module mới nạp vào monorepo xong → chạy `bash scripts/sync-modules-hub.sh <tên-module>` là tự có repo lẻ + cập nhật hub này.

## Kiến trúc chung
- **Multi-tenant:** mọi bảng có `org_id` + RLS fail-closed, mọi query filter org.
- **Manifest v2 strict:** loader validate tự động, module sai chuẩn bị từ chối nạp (không sập API).
- **Tiểu Tâm AI bao trùm:** module export tieu-tam-actions → tự động thành tool của trợ lý AI; tool trả `data.downloadUrl` → chat tự hiện nút tải file.
- **Outbox events:** module emit/subscribe event atomic qua manifest.
