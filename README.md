# experiencia-imersiva-Laura

Diário de bordo da eletiva **Experiências Imersivas** (Inteli XR). A cada aula registro o que fiz, o que entendi e uma dica para mim mesma no futuro.

O material de apoio da turma (template A-Frame + Caddy) está em [`Repositorio-Template-Caddy-AFrame-main/`](Repositorio-Template-Caddy-AFrame-main).

---

## Aula 1 — Genealogia da imersão (16/11)

Nessa aula teórica a gente percorreu a história da imersão, da mimese até o headset. Vimos a diferença entre Platão, para quem imitar é se afastar da verdade (a cama pintada está "três vezes longe" da cama real) e por isso é perigoso, e Aristóteles, para quem representar é uma forma de aprender. Depois passamos pela ideia de moldura: enquanto ela está à vista, a gente sabe que aquilo está "no lugar de" outra coisa; a ilusão acontece quando a imitação rompe a moldura. Vimos exemplos como a Villa dei Misteri em Pompeia, a perspectiva de Brunelleschi e Masaccio, o trompe l'oeil, os panoramas de Barker e o Panorama de Sedan, onde o público ficava preso numa plataforma a 12 metros da tela para não conseguir relativizar o que via. No fim fizemos a ficha do projeto (domínio, o que sentir e para quê, por que não numa tela, moldura, corpo e risco).

O que mais ficou para mim é que toda imersão esconde a moldura e prende o corpo num ponto, e o headset faz isso de um jeito novo: fixa a distância da tela, mas deixa o corpo livre no espaço. Isso quer dizer que quem projeta a experiência decide o que a pessoa vai sentir, e tem responsabilidade sobre isso. **Dica:** ao pensar no nosso projeto, responder sempre "por que isso não funcionaria numa tela comum?" — se a resposta for fraca, a experiência provavelmente não precisa ser imersiva.

## Aula 2 — Imersão, A-Frame e HTTPS com Caddy (16/11)

Essa aula foi de fundamentos e setup. Começamos com o cronograma da eletiva (proposta em 19/11, prova de conceito em 27/11, assets e moodboard em 04/12, vertical slice em 11/12 e apresentação final em 18/12) e com a diferença entre imersão e presença segundo Slater e Wilbur (1997): imersão é o que o sistema oferece (campo de visão, som, rastreamento) e pode ser medida; presença é a sensação subjetiva de "estar lá", que depende também da interação e da narrativa. Na parte prática vimos a menor cena possível em A-Frame (uma esfera, um plano e um céu), em que cada tag é uma entidade, os atributos são componentes e a unidade é o metro. Também vimos como servir a cena com o Caddy usando `tls internal`, que cria uma CA local e gera um certificado para o IP da máquina, permitindo abrir a cena no Quest ou no celular.

O ponto que eu entendi melhor foi o porquê do HTTPS: WebXR, câmera e microfone só funcionam em contexto seguro, e `localhost` é a única exceção. Então, para testar num dispositivo pela rede, é obrigatório ter HTTPS, e o aviso do navegador aparece porque a CA do Caddy não é conhecida, sendo preciso aceitar o certificado ou instalar o `root.crt` uma vez em cada dispositivo. O desafio do projeto é criar uma mecânica de lançamento sem usar as mãos. **Dica:** descobrir o IP da máquina na rede antes de tudo e colocá-lo no Caddyfile; se o acesso por IP falhar, testar a opção `default_sni` com o IP.
