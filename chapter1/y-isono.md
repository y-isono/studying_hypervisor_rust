# 1.1 仮想マシンとはなんだろう

ISA = Instruction Set Architecture: 命令セットアーキテクチャ。
ソフトウェアとハードウェアの境界として働いている。

OS は以前スーパーバイザーとも呼ばれており、それがハイパーバイザーの語源とされる。

ハイパーバイザは OS から物理デバイスを隠蔽し、仮想デバイスという形で実際のデバイスに対応するインターフェイスを OS に提供する。

# 1.2 ハイパーバイザの目的とメリット

ハイパーバイザーによるメリット:

- 複数の OS を動かせる
- ゲスト OS の動作環境を柔軟に変更できる

クラウド環境やサーバー環境と相性が良い。

# 1.3 Type1 ハイパーバイザと Type2 ハイパーバイザ

ハードウェア上にて直接動作し、その上でゲスト OS を実行する Type1 ハイパーバイザ (Xen、VMware ESXi など)、ホスト OS 上にで動作し、その上でゲスト OS を動作せる Type2 ハイパーバイザ (Oracle VirtualBox, QEMU-KVM など) が存在する。

＊ 自身の理解では KVM は type1 相当と考えていたが、KVM は type1 とも type2 とも言えるとのこと。

# 1.4 仮想化支援機構とは

逐次チェックのバイナリトランスレーションでは性能に課題があるので、cpu ハードウェア側で仮想化向けに提供されている便利機能のこと。
cpu 設定のみをすることでゲスト OS を安全に CPU で実行できるようになる。

AArch64 では、特権レベルとして例外レベル (Exception Level) が存在する。

- EL0
  - アプリケーション向け
- EL1
  - OS 向け
- EL2
  - ハイパーバイザー向け
- EL3
  - ファームウェア向け

仮想化支援機構のない cpu では EL2 で動作できなくなっている。

# 1.5 Type1 ハイパーバイザを開発する流れ

略

# 1.6 開発環境の構築

略

# 1.7 本書で使用する仕様書について

- Armアーキテクチャの仕様書
  - https://developer.arm.com/documentation/ddi0487/ka/
- GICの仕様書
  - https://developer.arm.com/documentation/ihi0069/hb/ 
- PL011の仕様書
  - https://developer.arm.com/documentation/ddi0183/g/
- PSCIの仕様書
  - https://developer.arm.com/documentation/den0022/fb/
- Devicetreeの仕様書
  - https://github.com/devicetree-org/devicetree-specification/releases/tag/v0.4 
- Virtioの仕様書
  - https://docs.oasis-open.org/virtio/virtio/v1.2/virtio-v1.2.pdf
- FAT32の仕様書
  - http://download.microsoft.com/download/0/8/4/084C452B-B772-4FE5-89BB-A0CBF082286A/fatgen103.doc 
- Linux起動の仕様書
  - https://www.kernel.org/doc/Documentation/arm64/booting.txt
