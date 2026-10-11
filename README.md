# How Positional Encoding Works

**위치 인코딩 — sin과 cos를 함께 쓰는 이유.** Transformer의 사인·코사인 위치 인코딩을 시계 바늘로 이해하는 인터랙티브 교육 자료입니다. 어텐션이 순서를 모르는 이유에서 출발해, sin과 cos를 짝으로 묶으면 위치가 원 위의 한 점이 되고 “k칸 이동”이 pos와 무관한 회전이 된다는 것을 브라우저에서 직접 확인합니다.

🔗 **[데모 바로가기](https://dev-jonghoonpark.github.io/how-positional-encoding-works/)**

## 다루는 내용

1. **어텐션은 순서를 모른다** · `dog bites man`을 섞어 넣어도 단어마다 받는 출력이 그대로인 실험
2. **사인·코사인 위치 인코딩** · 원논문 식과 히트맵
3. **sin 하나로는 부족하다** · 한 주기 안에서 같은 sin 값이 두 번 나오는 모호함
4. **시계 바늘** · (sin, cos)는 12시에서 시작해 시계 방향으로 도는 바늘, d<sub>model</sub>=16의 시계 8개
5. **k칸 이동 = 회전 행렬** · M<sub>k</sub>·PE(pos) = PE(pos+k)를 숫자로 검증, sin만으로는 점들이 직선이 아니라 타원을 그리는 이유
6. **크기와 내적** · ‖PE‖ = √(d/2)로 일정, PE(pos)·PE(pos+k) = Σcos(ω<sub>i</sub>k)라 기준 위치를 바꿔도 곡선이 정확히 겹침
7. **시계가 여러 개인 이유** · 주기 2π ~ 2π·10000, 초침·분침·시침
8. **RoPE** · q, k를 위치만큼 돌리면 점수에 n − m만 남는 것
9. **퀴즈** 5문항

## 참고

- Vaswani 외 (2017), *Attention Is All You Need* — [arXiv:1706.03762](https://arxiv.org/abs/1706.03762)
- Su 외 (2021), *RoFormer: Enhanced Transformer with Rotary Position Embedding* — [arXiv:2104.09864](https://arxiv.org/abs/2104.09864)

[how-ai-works](https://github.com/dev-jonghoonpark/how-ai-works) 시리즈의 일부입니다.
