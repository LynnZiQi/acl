# Matinee fight scene performance

To compile these statistics, the [Matinee fight scene](http://nfrechette.github.io/2017/10/05/acl_in_ue4/) is used.

*  Number of clips: **5**
*  Sample rate: **30 FPS**
*  Cinematic duration: **66 seconds**
*  *Troopers* 1-4 have **71** bones and the *Main Trooper* has **551** bones
*  Raw size: **62.38 MB** (10x float32 * num bones * num samples)

ACL supports various compression methods but only the overall best variant will be tracked here (see `get_default_compression_settings()` for details).

The error is measured **3cm** away from each bone to simulate the visual mesh skinning process as described [here](error_metrics.md).

The performance of ACL in Unreal Engine 4 is tracked by the plugin [here](https://github.com/nfrechette/acl-ue4-plugin/blob/develop/Docs/fight_scene_performance.md).

|         | ACL v1.0.0 |
| ------- | -------- |
| **Compressed size** | 8.66 MB |
| **Compression ratio**    | 7.20 : 1 |
| **Max error**                  | 0.0618 cm |
| **Compression time**     | 02m 08.14s |

