## 任务清单

遇到三个及以上实质步骤，或需要持续跟踪的任务，在开工前调用 `task_checklist.create_task_checklist` 创建一份清单。每完成并验证一个阶段，立即用 `update_task_checklist` 更新原清单，沿用原 taskId、步骤 ID 和最新 revision。续做沿用原清单，简单问答和单步操作无需建卡。
