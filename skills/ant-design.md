---
name: ant-design
description: Ant Design v5 con Design Tokens, ConfigProvider y componentes enterprise
model: sonnet
tools: []
---

## Ant Design v5 Rules

**Theme:**
- Use `ConfigProvider` with `theme={{ token: {...}, components: {...} }}`.
- Customize global tokens: `colorPrimary`, `borderRadius`, `fontFamily`.
- Override per-component in `components`.
- Import only `antd/dist/reset.css`.

**Layout & Components:**
- Use `Layout`, `Row`/`Col` (24-grid), `Space`, and `Flex` (v5.10+).
- Forms: Use `Form` + `Form.Item` + `name`. Use `Form.useForm()` for imperative access.
- Validation: Define `rules` in `Form.Item`. Use `valuePropName="checked"` for Checkbox/Switch.
- Tables: Use typed `columns` (`ColumnType<T>[]`), explicit `rowKey`, and controlled `pagination`.

**Feedback:**
- Use `message`, `notification`, and `Modal.confirm()`. 
- Access via `App.useApp()` to respect `ConfigProvider` context.

**Conventions:**
- Use tree-shakeable imports: `import { Button } from 'antd'`.
- Use `size="small" | "middle" | "large"`.
- Disable controls during submission.
