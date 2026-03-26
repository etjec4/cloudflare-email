# Cloudflare Email 项目进度

## 已完成
- [x] 开发环境初始化
- [x] 多配置管理功能实现
- [x] 邮件解析与基础显示
- [x] 邮件发送功能

## 架构字典
- `store/use-configs.ts`: 多配置管理 Store，支持添加、修改、删除和切换配置。
- `store/use-settings.ts`: 系统级设置 Store，提供获取激活配置设置的工具函数。
- `app/api/send/route.ts`: 后端发送邮件接口，调用 Resend API。
- `components/mail/mail-editor.tsx`: 邮件编辑器组件，负责调用前端发送逻辑。
- `components/settings/settings-dialog.tsx`: 系统设置对话框，支持多配置编辑。

## 函数字典
### `store/use-configs.ts`
- `addConfig`: 添加新配置。
- `updateConfig`: 更新现有配置。
- `deleteConfig`: 删除配置。
- `setActiveConfig`: 设置当前激活的配置 ID。
- `getActiveConfig`: 获取当前激活的配置对象。

### `store/use-settings.ts`
- `getActiveSettings`: 获取当前有效的 API 设置（优先从激活配置中获取）。

### `components/mail/mail-editor.tsx`
- `handleSend`: 处理邮件发送逻辑，构建 HTML 内容并调用 API。

## 待处理
- [x] 修复多配置下发送邮件无法正确匹配 Resend API key 的问题。
- [x] 在 `use-settings.ts` 中增加 `useActiveSettings` 响应式 Hook，简化配置调用。

## 错误/交互日志
- `MailEditor` 直接引用 `useSettings` 的状态变量 `resendApiKey`，而非通过激活配置进行动态匹配。
- `EmailSwitcher.tsx` 缺少 `useActiveSettings` 的导入导致编译失败，已修复。

## 关联映射
- `多配置切换 -> 邮件发送 Resend API Key 匹配调整`
