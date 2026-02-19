---
title: Launch File Integration
weight: 4
---

LGDXRobot Cloud Adapter has the following parameters that can be set in the launch file.

| Parameter Name | Type | Description |
| --- | --- | --- |
| slam_enable | bool | Enables or disables SLAM mode. |
| address | string | Address of the LGDXRobot Cloud. |
| root_cert | string | Path to the server root certificate. |
| client_key | string | Path to the client's private key. |
| client_cert | string | Path to the client's certificate chain. |
| need_mcu_sn | bool | Require MCU Serial Number before connecting to the cloud. |
{.table}

An example of the launch file is shown below.

```python
lgdxrobot_cloud_node = Node(
  package='lgdxrobot_cloud_adapter',
  executable='lgdxrobot_cloud_adapter_node',
  condition=IfCondition(use_cloud),
  output='screen',
  parameters=[{
    'need_mcu_sn': True,
    'slam_enable': slam,
    'address': cloud_address,
    'client_key': cloud_client_key,
    'client_cert': cloud_client_cert,
    'root_cert': cloud_root_cert,
  }],
)
```

The LGDXRobot Cloud Adapter can run as a composable node.
{.alert .alert-info}
