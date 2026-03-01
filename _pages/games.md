---
title: "GAMES"
layout: splash
permalink: /games/
---

<style>
.games-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 24px;
  margin-top: 2em;
}
.game-card {
  background: #fff;
  border: 1px solid #e0e0e0;
  border-radius: 12px;
  padding: 32px 24px;
  width: 260px;
  text-align: center;
  box-shadow: 0 2px 8px rgba(0,0,0,0.07);
  transition: box-shadow 0.2s;
}
.game-card:hover {
  box-shadow: 0 6px 20px rgba(0,0,0,0.13);
}
.game-icon {
  font-size: 3em;
  margin-bottom: 12px;
}
.game-card h3 {
  margin: 0 0 10px;
  font-size: 1.2em;
}
.game-card p {
  font-size: 0.92em;
  color: #555;
  margin-bottom: 20px;
}
</style>

<div class="games-grid">
  <div class="game-card">
    <div class="game-icon">🎮</div>
    <h3>숫자 맞추기</h3>
    <p>1~100 사이의 숫자를 10번 안에 맞춰보세요!</p>
    <a href="https://dermut.github.io/guessing_number/" class="btn btn--primary btn--large">플레이하기</a>
  </div>
</div>
