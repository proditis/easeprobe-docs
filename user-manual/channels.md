---
description: Probe and Notification channels
---

# 4. Channel

The Channel is used for connecting the Probers and the Notifiers. It can be configured for every Prober and Notifier.

This feature could help you group the Probers and Notifiers into a logical group.

> **Note**:
>
> If no Channel is defined on a probe or notify entry, then the default channel will be used. The default channel name is `__EaseProbe_Channel__`
>
> EaseProbe versions prior to v1.5.0, do not have support for the `channel` feature

### 4.2 Examples

For example:

```
http:
   - name: probe A
     channels : [ Dev_Channel, Manager_Channel ]
shell:
   - name: probe B
     channels: [ Ops_Channel ]
notify:
   - discord: Discord
     channels: [ Dev_Channel, Ops_Channel ]
   - email: Gmail
     channels: [ Mgmt_Channel ]
```

Then, we will have the following diagram

```
┌───────┐          ┌──────────────┐
│Probe B├─────────►│ Mgmt_Channel ├────┐
└───────┘          └──────────────┘    │
                                       │
                                       │
                   ┌─────────────┐     │   ┌─────────┐
            ┌─────►│ Dev_Channel ├─────▼───► Discord │
            │      └─────────────┘         └─────────┘
┌───────┐   │
│Probe A├───┤
└───────┘   │
            │      ┌────────────┐          ┌─────────┐
            └─────►│ QA_Channel ├──────────►  Gmail  │
                   └────────────┘          └─────────┘
```
