Endereços de memória usados
246 = botão direção (0: horário, 1: anti-horário)
247 = botão velocidade (0: rápido, 1: lento)
248 = bobina 1
249 = bobina 2
250 = bobina 3
251 = bobina 4
252 = valor do delay lento
253 = valor de manipulação
254 = valor 0 
255 = valor 1 para somar e subtrair


INICIO 
00 = 32 LDA
01	246 -> Lê a direção

HORARIO
02 = 160 JZ -> se o acumulador for 0 pula para "6"
03     6

ANTI HORARIO
04 = 148 JP -> se o acumulador for positivo pula "110"
05     110

MOTORES HORARIO
MOTOR1
06 = 32 LDA
07	 255 -> carrega o 1 para o acumulador
08 = 16 STA
09   248 -> liga motor 1
10 = 32 LDA
11   254 -> carrega o 0 para o acumulador
12 = 16 STA
13   248 -> desliga motor 1

DELAY
14 = 32 LDA
15   247 -> lê velocidade
16 = 160 JZ
17   32 -> PULA PARA MOTOR2 CASO VELOCIDADE SEJA 0 "RAPIDO"
18 = 32 LDA
19	 252 -> carrega o valor de delay
20 = 16 STA
21 	 253 -> escreve o valor de delay para manipulação
22 = 32 LDA
23   253 -> carrega o valor vigente para inicio do loop
24 = 112 SUB
25   255 -> diminui 1 do valor de manipulação
26 = 16 STA
27 	 253 -> sobreescreve o valor de delay para manipulação
28 = 160 JZ
29   32 -> PULA PARA MOTOR2
30 = 128 JMP
31	 22

MOTOR2
32 = 32 LDA
33	 255 -> carrega o 1 para o acumulador
34 = 16 STA
35   249 -> liga motor 2
36 = 32 LDA
37   254 -> carrega o 0 para o acumulador
38 = 16 STA
39   249 -> desliga motor 2

DELAY
40 = 32 LDA
41   247 -> lê velocidade
42 = 160 JZ
43   58 -> PULA PARA MOTOR3 CASO VELOCIDADE SEJA 0 "RAPIDO"
44 = 32 LDA
45	 252 -> carrega o valor de delay
46 = 16 STA
47 	 253 -> escreve o valor de delay para manipulação
48 = 32 LDA
49   253 -> carrega o valor vigente para inicio do loop
50 = 112 SUB
51   255 -> diminui 1 do valor de manipulação
52 = 16 STA
53 	 253 -> sobreescreve o valor de delay para manipulação
54 = 160 JZ
55   58  -> PULA PARA MOTOR3
56 = 128 JMP
57	 49

MOTOR3
58 = 32 LDA
59	 255 -> carrega o 1 para o acumulador
60 = 16 STA
61   250 -> liga motor 3
62 = 32 LDA
63   254 -> carrega o 0 para o acumulador
64 = 16 STA
65   250 -> desliga motor 3

DELAY
66 = 32 LDA
67   247 -> lê velocidade
68 = 160 JZ
69   84 -> PULA PARA MOTOR4 CASO VELOCIDADE SEJA 0 "RAPIDO"
70 = 32 LDA
71	 252 -> carrega o valor de delay
72 = 16 STA
73 	 253 -> escreve o valor de delay para manipulação
74 = 32 LDA
75   253 -> carrega o valor vigente para inicio do loop
76 = 112 SUB
77   255 -> diminui 1 do valor de manipulação
78 = 16 STA
79 	 253 -> sobreescreve o valor de delay para manipulação
80 = 160 JZ
81   84 -> PULA PARA MOTOR4
82 = 128 JMP
83	 75

MOTOR4
84 = 32 LDA
85	 255 -> carrega o 1 para o acumulador
86 = 16 STA
87   251 -> liga motor 4
88 = 32 LDA
89   254 -> carrega o 0 para o acumulador
90 = 16 STA
91   251 -> desliga motor 4

DELAY
92 = 32 LDA
93   247 -> lê velocidade
94 = 160 JZ
95   06 -> PULA PARA MOTOR1 CASO VELOCIDADE SEJA 0 "RAPIDO"
96 = 32 LDA
97	 252 -> carrega o valor de delay
98 = 16 STA
99 	 253 -> escreve o valor de delay para manipulação
100= 32 LDA
101  253 -> carrega o valor vigente para inicio do loop
102= 112 SUB
103   255 -> diminui 1 do valor de manipulação
104= 16 STA
105	 253 -> sobreescreve o valor de delay para manipulação
106= 160 JZ
107  06 -> PULA PARA MOTOR1
108= 128 JMP
109	 101

MOTORES ANTIHORARIO
MOTOR4
110= 32 LDA
111	 255 -> carrega o 1 para o acumulador
112= 16 STA
113  251 -> liga motor 4
114= 32 LDA
115  254 -> carrega o 0 para o acumulador
116= 16 STA
117  251 -> desliga motor 4

DELAY
118= 32 LDA
119  247 -> lê velocidade
120= 160 JZ
121  136 -> PULA PARA MOTOR3 CASO VELOCIDADE SEJA 0 "RAPIDO"
122= 32 LDA
123	 252 -> carrega o valor de delay
124= 16 STA
125	 253 -> escreve o valor de delay para manipulação
126= 32 LDA
127  253 -> carrega o valor vigente para inicio do loop
128= 112 SUB
129  255 -> diminui 1 do valor de manipulação
130= 16 STA
131  253 -> sobreescreve o valor de delay para manipulação
132= 160 JZ
133  136 -> PULA PARA MOTOR3
134= 128 JMP
135	 127

MOTOR3
136= 32 LDA
137	 255 -> carrega o 1 para o acumulador
138= 16 STA
139  250 -> liga motor 3
140= 32 LDA
141  254 -> carrega o 0 para o acumulador
142= 16 STA
143  250 -> desliga motor 3

DELAY
144= 32 LDA
145  247 -> lê velocidade
146= 160 JZ
147  162 -> PULA PARA MOTOR2 CASO VELOCIDADE SEJA 0 "RAPIDO"
148= 32 LDA
149	 252 -> carrega o valor de delay
150= 16 STA
151	 253 -> escreve o valor de delay para manipulação
152= 32 LDA
153  253 -> carrega o valor vigente para inicio do loop
154= 112 SUB
155  255 -> diminui 1 do valor de manipulação
156= 16 STA
157	 253 -> sobreescreve o valor de delay para manipulação
158= 160 JZ
159  162 -> PULA PARA MOTOR2
160= 128 JMP
161	 153

MOTOR2
162= 32 LDA
163	 255 -> carrega o 1 para o acumulador
164= 16 STA
165  249 -> liga motor 2
166= 32 LDA
167  254 -> carrega o 0 para o acumulador
168= 16 STA
169  249 -> desliga motor 2

DELAY
170= 32 LDA
171  247 -> lê velocidade
172= 160 JZ
173  188 -> PULA PARA MOTOR1 CASO VELOCIDADE SEJA 0 "RAPIDO"
174= 32 LDA
175	 252 -> carrega o valor de delay
176= 16 STA
177  253 -> escreve o valor de delay para manipulação
178= 32 LDA
179  253 -> carrega o valor vigente para inicio do loop
180= 112 SUB
181  255 -> diminui 1 do valor de manipulação
182= 16 STA
183	 253 -> sobreescreve o valor de delay para manipulação
184= 160 JZ
185  188 -> PULA PARA MOTOR1
186= 128 JMP
187	 179

MOTOR1
188= 32 LDA
189	 255 -> carrega o 1 para o acumulador
190= 16 STA
191  248 -> liga motor 1
192= 32 LDA
193  254 -> carrega o 0 para o acumulador
194= 16 STA
195  248 -> desliga motor 1

DELAY
196= 32 LDA
197  247 -> lê velocidade
198= 160 JZ
199  110 -> PULA PARA MOTOR1 CASO VELOCIDADE SEJA 0 "RAPIDO"
200= 32 LDA
201	 252 -> carrega o valor de delay
202= 16 STA
203	 253 -> escreve o valor de delay para manipulação
204= 32 LDA
205  253 -> carrega o valor vigente para inicio do loop
206= 112 SUB
207  255 -> diminui 1 do valor de manipulação
208= 16 STA
209	 253 -> sobreescreve o valor de delay para manipulação
210= 160 JZ
211  110 -> PULA PARA MOTOR4
212= 128 JMP
213	 205
