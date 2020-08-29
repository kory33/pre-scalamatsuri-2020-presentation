---
marp: true
---

<style>
section {
  font-size: 30px;
}
</style>

# **1万行のKotlinをScalaに移行した話**

## How I migrated 10k Kotlin lines to Scala

by kory33 (@Kory__3)

---

# Self-Introduction

---

# Self-Introduction

 - ## 学部一年生(夏休み中)
   - ### 数学+CSをやっています
     A first-year undergraduate studying Math+CS, currently on a vacation
 - ## Ubie社でインターン 
   internship at Ubie Inc.
 - ## 整地サーバー運営
   Server dev-admin at Seichi Server

---

# Seichi Server？　　　　　![整地鯖](./resources/seichi-server-logo-low-res.png)

---

# Seichi Server (Officially *Gigantic Seichi Server*)

 - 日本で最も大きな公開Minecraftサーバーの一つ
   One of the largest public Minecraft servers in Japan

 - Minecraftを拡張し、プレーヤーが**大量に**ブロックを破壊できるように
   The game is tweaked; players can break **a lot** of blocks

(Seichi stands for grading, levelling the ground)

---

![整地鯖](./resources/seichi-server-skill-enlarged.gif)
「整地スキル」使用中のプレーヤー / a player using *Seichi skill*

---

# SeichiAssist

[https://github.com/GiganticMinecraft/SeichiAssist](https://github.com/GiganticMinecraft/SeichiAssist)

---

# SeichiAssist

 - ブロックを壊すだけではなく、それに付随する様々な基盤がくっついている
   The server has many subsystems, not necessarily related to breaking blocks

 - これらの基盤の**すべて**を任されているのが SeichiAssist というソフトウェア
   *SeichiAssist* is a software that handles *all* concerns of this large system

---

# SeichiAssist - at the beginning of year 2018

 - システムはどんどん複雑化し、バグが混入しても容易にfixできなくなった
   The growing system had become too complex; bugfix was very difficult

 - 機能開発をほぼ止めてリファクタリング/再実装に注力しようという話になったのが2018年初頭
   The beginning of 2018 was when the team decided to concentrate on refactoring / reimplementation rather than adding new features

---

# So we moved to Kotlin ... at first

 - Kotlinへの移行はとても楽
   Migration to Kotlin from Java is easy

 - IntelliJ IDEAに入っているJava -> Kotlinのコンバータの精度がとても良い
   IntelliJ IDEA provides a very accurate Java-to-Kotlin converter

 - Java -> Scalaのコンバータは割と動かないコードを吐いた
   Java-to-Scala converter by IntelliJ often yielded code that doesn't compile

 - チームでKotlinの方が書ける人が多かった
   The dev team was more comfortable with Kotlin than with Scala

