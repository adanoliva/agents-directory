---
name: ant-design
description: Ant Design v5 con Design Tokens, ConfigProvider y componentes enterprise
model: sonnet
tools: []
---

## Technology context — Ant Design v5

This project uses **Ant Design v5** (`antd`).

**Theme configuration:**
- `ConfigProvider` at root with `theme={{ token: {...}, components: {...} }}`
- Customize global tokens: `colorPrimary`, `borderRadius`, `fontFamily`, `colorBgContainer`…
- Per-component overrides in `components`: `{ Button: { colorPrimary: '...' } }`
- Don't import global styles (`import 'antd/dist/reset.css'` is enough with v5)

```tsx
<ConfigProvider theme={{
  token: { colorPrimary: '#6366f1', borderRadius: 8 },
  components: { Button: { fontWeight: 600 } },
  algorithm: theme.darkAlgorithm,  // dark mode
}}>
  <App />
</ConfigProvider>
```

**Layout:**
- `Layout`, `Layout.Header`, `Layout.Sider`, `Layout.Content`, `Layout.Footer` for page structures
- `Row` + `Col` for 24-column grid: `<Col span={12} xs={24} md={12}>`
- `Space` to group elements with uniform gap; `Space.Compact` for input groups
- `Flex` (v5.10+) for declarative flexbox layouts

**Forms:**
- Always use `Form` + `Form.Item` + `name` prop — enables validation, reset and `setFieldsValue`
- `Form.useForm()` for imperative form access
- Validation rules in `rules={[{ required: true, message: '...' }]}`
- `Form.Item` with `valuePropName="checked"` for Checkbox and Switch

```tsx
const [form] = Form.useForm()
<Form form={form} onFinish={handleSubmit} layout="vertical">
  <Form.Item name="email" label="Email" rules={[{ required: true, type: 'email' }]}>
    <Input />
  </Form.Item>
</Form>
```

**Tables:**
- `Table` with typed `columns` (`ColumnType<T>[]`) and `dataSource`
- Always explicit `rowKey`: `rowKey="id"` or `rowKey={(r) => r.id}`
- Controlled pagination for large datasets: `pagination={{ current, pageSize, total, onChange }}`
- `sorter` and `filters` on columns for server-side sorting/filtering

**User feedback:**
- `message.success/error/loading()` for brief global notifications
- `notification.open()` for more elaborate or persistent messages
- `Modal.confirm()` for destructive action confirmations
- `App.useApp()` (v5) to access `message`, `notification` and `modal` respecting the ConfigProvider context

**Conventions:**
- Tree-shakeable imports: `import { Button, Table } from 'antd'` — the Vite plugin optimizes this
- `size="small" | "middle" | "large"` for size consistency
- `disabled` on controls during submission to prevent double-submit
