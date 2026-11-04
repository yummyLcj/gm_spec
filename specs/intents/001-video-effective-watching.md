<!-- SPDX-License-Identifier: Apache-2.0 -->
<!-- SPDX-FileCopyrightText: 2026 chenjieLu <luchenjie@gumingnc.com> -->

# IR-001: 视频有效观看检测

## 状态

待实施

## 意图

按照 [DR-001](../decisions/001-video-effective-watching.md) 实现 [[video-watching-1](../packages/video-watching.md#video-watching-1)] 至 [[video-watching-12](../packages/video-watching.md#video-watching-12)]，形成可复用的视频有效观看检测能力。

## 交付项

- [ ] 前端观看状态模型、播放器事件适配器和页面可见性检测
- [ ] 前端观看会话管理、心跳调度和播放器集成
- [ ] 后端会话、心跳校验、有效时长和观看区间持久化能力
- [ ] 会话超时和网络恢复处理
- [ ] 覆盖规约验证条目的集成测试和系统测试

## 任务

1. 定义观看状态、检测配置、会话和心跳的数据契约，并提交 `feat(watching): define watching contracts`。

2. 实现播放器事件与页面可见性的统一状态判定，并提交 `feat(watching): track effective playback state`。

3. 实现观看会话的创建、结束、鉴权和归属校验，并提交 `feat(watching): add watching sessions`。

4. 实现前端心跳调度、单调序号和生命周期清理，并提交 `feat(watching): send watching heartbeats`。

5. 实现服务端心跳的权限、顺序、时间窗口和播放证据校验，并提交 `feat(watching): validate watching heartbeats`。

6. 实现播放位置、有效时长和已观看区间的独立持久化及区间合并，并提交 `feat(watching): persist effective progress`。

7. 实现会话超时、断线恢复和视频切换隔离，并提交 `feat(watching): handle session recovery`。

8. 将检测模块接入现有播放器并清理组件卸载或视频切换时的资源，并提交 `feat(watching): integrate video player`。

9. 实现规约要求的真实前后端集成与端到端场景，并提交 `test(watching): verify effective watching`。

## 验证

- `npx @sublang/spex lint` 通过。
- [[video-watching-13](../packages/video-watching.md#video-watching-13)] 至 [[video-watching-18](../packages/video-watching.md#video-watching-18)] 通过。
- 现有视频播放、暂停、倍速和断点续播能力无回归。
- 规约、实现和系统测试对有效观看判定及统计口径保持一致。
