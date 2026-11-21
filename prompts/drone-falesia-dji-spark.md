# Drone 1 Creator® — Falésia com pessoas (DJI Spark, ~12 s)

Imagem de referência: falésia de rocha escura em colunas, topo de grama verde, 6 pessoas na borda, mar turquesa à direita, céu azul com nuvens alongadas.

---

## 1. Prompt principal (EN — funciona melhor no Grok Imagine, Sora, Veo, Kling, Runway, Luma)

```
Image-to-video, use the uploaded photo as the first frame. Preserve the exact location:
dark columnar basalt sea cliff, flat green grass top, six people standing near the edge,
turquoise ocean on the right, deep blue sky with long streaks of white cloud.

Shot on a small consumer drone (DJI Spark style), 4K, 30 fps, sharp detail, natural
sunlight, slight wide-angle lens, realistic gimbal stabilization, subtle propeller wind.

Duration ~12 seconds, one continuous shot, no cuts:

0–3 s: Drone starts low and far from the cliff face, drifting forward very slowly and
smoothly. Calm, cinematic, gentle push-in toward the people on the edge.

3–6 s: Drone gradually accelerates, rising along the rock face; texture of the stone
columns rushes past at the bottom of the frame.

6–8 s: Drone speeds up a lot and races straight toward the group of people at eye level.
The people notice it, their faces turn surprised and startled, wide eyes, some raise
their arms, and they duck and crouch down as the drone zips just over their heads.

8–10 s: Drone banks and performs a fast, smooth 180° orbit around the group, people still
crouching and looking up at it, grass flattened by propeller wash.

10–12 s: Drone pulls away and climbs, flying along the rest of the clifftop and tilting up
toward the open blue sky and clouds, ocean sparkling below. Ending on wide sky.

Speed ramp: slow -> medium -> fast. Realistic motion blur only at the fastest moment.
Keep the people's appearance, clothes and positions consistent. Photorealistic,
no text, no watermark, no distortion of faces or limbs.
```

## 2. Versão em português (para modelos que aceitam PT)

```
Imagem para vídeo, usando a foto enviada como primeiro quadro. Mantenha o local idêntico:
falésia de rocha escura em colunas, topo de grama verde, seis pessoas na borda, mar
turquesa à direita, céu azul com nuvens brancas alongadas.

Filmado por um drone DJI Spark, 4K, 30 fps, alta nitidez, luz do sol natural,
estabilização de gimbal realista.

Duração de ~12 segundos, plano contínuo, sem cortes:
0–3 s: o drone se aproxima devagar, suave e cinematográfico.
3–6 s: acelera um pouco, subindo junto à parede de rocha.
6–8 s: acelera bastante e vai muito rápido em direção às pessoas; elas ficam com cara de
assustadas, olhos arregalados, e se abaixam quando o drone passa rente sobre elas.
8–10 s: o drone faz uma volta rápida (órbita) ao redor do grupo; as pessoas, ainda
abaixadas, olham para cima.
10–12 s: o drone se afasta e sobe, seguindo pelo resto da montanha e virando para o céu
aberto com nuvens, terminando num plano amplo do céu.

Fotorrealista, rostos e roupas consistentes, sem texto, sem marca d'água.
```

## 3. Negative prompt (se o modelo aceitar)

```
cartoon, CGI look, warped faces, extra limbs, morphing people, people falling off the cliff,
camera cuts, shaky handheld, text, logo, watermark, low resolution, flicker
```

## 4. Dicas de uso

- **Grok Imagine (app/X)**: envie a foto, cole o prompt EN, escolha modo vídeo. Se cortar em ~6 s,
  gere em duas partes: (A) 0–8 s até as pessoas se abaixarem; (B) use o último quadro de A
  como imagem inicial para a órbita + subida ao céu, e junte no CapCut/DaVinci.
- **Kling / Runway / Veo / Sora**: permitem 10–12 s direto; use "camera motion: push-in → orbit → crane up".
- Se o rosto "assustado" não aparecer, adicione: `close enough to see their startled expressions`.
- Velocidade: se o modelo ignorar a aceleração, faça o speed ramp na edição (0,7x → 1x → 1,6x).
