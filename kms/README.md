# KMS

## struct

階層を持つ
1. project
2. location [doc](https://cloud.google.com/kms/docs/locations?hl=ja)
  - 距離が近いほうが信頼性と速度が上がる
  - globalなら近いところで自動でやるが書き込みには伝播に時間がかかる
    - 読み取りが世界各地 + 書き込みが少ないならばglobalを選ぶほうがよい
3. keyring
4. key
5. version