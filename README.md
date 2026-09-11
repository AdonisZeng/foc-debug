# foc-debug

一个自己在开发中不断总结的 FOC 电机开发调试 skill。

## 结构

```
foc-debug/
├── SKILL.md                          # 入口：使用原则 + 通用调试流程 + 故障现象索引
├── references/
│   ├── diagnostic-cards/             # 排查卡：按调试阶段/物理根源聚合
│   │   ├── startup.md                #   启动流程（预定位→强拖→切入）
│   │   ├── observer-lock.md          #   观测器锁定（SMO/PLL）
│   │   ├── speed-loop.md             #   速度环（转速控制/转速限制）
│   │   ├── current-loop.md           #   电流环
│   │   └── sampling-modulation.md    #   采样与调制（死区/管压降）
│   └── motor-profiles/               # 电机实例档案：按具体电机记录
│       ├── template.md               #   档案模板
│       ├── vacuum-motor.md           #   吸尘器电机（一对极，带风机叶片）
│       ├── hobby-motor.md            #   航模电机（低电感，空载）
│       ├── fan-motor.md              #   36V 风机电机（五对极，大惯量扇叶，无感）
│       ├── hv-fan-motor.md           #   高压风扇电机（25W 旧电机，RY7212 霍尔平台）
│       └── pm5408-motor.md           #   PEMS PM5408（75W 新电机，RY7212 霍尔平台，适配中）
├── LICENSE
└── README.md
```

## 设计理念

- **现象驱动**：调试入口是"故障现象"不是"电机类型"，SKILL.md 的故障现象索引直接
  映射到对应排查卡。
- **物理根源聚合**：排查卡按物理根源聚合，每个坑带"适用标签"（电机特性元数据），
  同一经验可被多类型电机复用。
- **电机实例档案**：按具体电机实例记录参数和踩坑经验，作为对照库。调新电机时先翻
  档案找最接近的实例，差异点就是排查方向。
