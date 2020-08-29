### Key Management 密钥管理

Content trust is directly associated with an image tag and each repository has a set of keys that publishers use to sign each image.

通过镜像标签，并且每一个镜像仓库都设置了密钥集合，用于提供发布者签名镜像。

A repository can have both unsigned and signed images. They live as separate entities, so the same tag (e.g. `latest`) can point to different contents depending on whether Docker Content Trust is enabled or not on the client.

镜像仓库可以同时有签名和未签名的镜像，它们分开存放，因此相同（ 例如：`latest`）标签镜像可以指向不同的内容，基于Docker内容信任是否启用或者不再与客户端？

Image trust builds on 4 keys:

镜像信任基于四个密钥：

- A `root` key (_offline_) which is the root anchor of the content trust for an image. This is key that gets stored on the Yubikey and only brought online for a limited number of operations

“根”密钥（离线）作为镜像内容信任的根，这个密钥通常存储于Yubikey并且仅在有限的操作次数下用于在线使用。

- A `targets` key (_online_) - the key that signs the actual files downloaded, stored on the client and encrypted at rest

“目标”密钥（在线）用于签名实际的文件下载，平时被加密存储于客户端。

- A `snapshot` key (_online_), which signs the metadata file containing information about all the other metadata available on the collection

“快照”密钥（在线）用于签名文件元数据，这些元数据文件包括所有其他类型的元数据 collection？？？

- A `timestamp` key (_online_), which ensures content freshness by periodically signing a timestamped statement.

“时间戳”密钥（在线）用于周期性的签名时间戳语句确保内容时效性。

The `snapshot` and the `timestamp` can be managed by the Notary service for convenience.

为了方便，“快照”密钥和“时间戳”密钥可以被Notary service服务托管。
