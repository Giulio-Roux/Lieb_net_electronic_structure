<img src="./header.jpg"/>

<h1 align="center">
Estrutura Eletrônica da Rede de Lieb
</h1>

<p align="center">
  <i>Modelo tight-binding da Rede de Lieb 2D: bandas, banda plana, densidade de estados e ocupação eletrônica usando PythTB.</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.12-blue">
  <img src="https://img.shields.io/badge/PythTB-2.0-orange">
  <img src="https://img.shields.io/badge/Área-Física%20da%20Matéria%20Condensada-darkgreen">
</p>

---

# Sobre o repositório

Este repositório contém um trabalho sobre a estrutura eletrônica da **Rede de Lieb** realizado para a disciplina de Matéria Condensada do curso de Bacharelado em Ciência e Tecnologia da Ilum - Escola de Ciência.

O objetivo do projeto é explorar a influência das energias *on-site* e do *hopping* entre próximos vizinhos na estrutura eletrônica da Rede de Lieb, um sistema que realiza estados exóticos da matéria e que foi construído experimentalmente em superfícies metálicas (Slot *et al.*, *Nature Physics* 13, 672–676, 2017).

O trabalho está descrito no relatório em PDF, e os cálculos estão no notebook `lieb_net.ipynb`. Para quatro casos (energias *on-site* iguais ou diferentes, *hopping* de próximos vizinhos nulo ou não nulo), são apresentadas as seguintes análises:

- estrutura da rede e caminho percorrido na Zona de Brillouin;
- estrutura de bandas ao longo de $\Gamma - X - M - \Gamma$;
- contribuição dos orbitais atômicos em cada banda (*fat bands*);
- densidade de estados (DOS) global de uma célula unitária;
- densidade de estados local (LDOS), por sítio;
- ocupação eletrônica, $D(E)f(E)$, com a distribuição de Fermi-Dirac.

📄 **Relatório:** [`Relatorio_Rede_de_Lieb.pdf`](https://drive.google.com/file/d/1Lb_1Nb8_d7JD7JUFMyoYbta2rVem9Y2B/view?usp=sharing)

---

# Conteúdos do repositório

<ul>
  <li> :framed_picture: <b>header.jpg</b>: imagem utilizada no cabeçalho do README.</li>
  <li> :page_facing_up: <b>lieb_net.ipynb</b>: notebook com todo o código: montagem do modelo no PythTB, bandas, <i>fat bands</i>, DOS, LDOS, ocupação eletrônica e caminho na Zona de Brillouin.</li>
  <li> :page_facing_up: <b>Relatorio_Rede_de_Lieb.pdf</b>: relatório do trabalho, com introdução teórica, metodologia, resultados, discussão e conclusões.</li>
  <li> :file_folder: <b>Resultados</b>: figuras geradas pelo notebook.</li>
  <ul>
    <li> :framed_picture: <b>estrutura.pdf</b>: célula unitária da rede com <i>hopping</i> de próximos vizinhos nulo e não nulo.</li>
    <li> :framed_picture: <b>caminho_zb.pdf</b>: Zona de Brillouin com os pontos de alta simetria e o caminho $\Gamma - X - M - \Gamma$.</li>
    <li> :framed_picture: <b>bandas.pdf</b>: estrutura de bandas dos quatro casos.</li>
    <li> :framed_picture: <b>fatbands.pdf</b>: contribuição de cada orbital (A, B<sub>x</sub>, B<sub>y</sub>) em cada banda.</li>
    <li> :framed_picture: <b>dos.pdf</b>: densidade de estados global de uma célula unitária.</li>
    <li> :framed_picture: <b>ldos.pdf</b>: densidade de estados local (por sítio).</li>
    <li> :framed_picture: <b>dos_ocupacao.pdf</b>: densidade de estados e ocupação eletrônica, $D(E)f(E)$.</li>
  </ul>
  <li> :page_facing_up: <b>LICENSE</b>: licença GPL-3.0.</li>
</ul>

---

# Como executar

O notebook utiliza a API da versão 2 do **PythTB** (`Lattice` e `TBModel`). Para instalar as dependências:

```bash
pip install "pythtb>=2.0" numpy scipy matplotlib jupyter
```

Em seguida, abra o notebook e execute todas as células:

```bash
jupyter notebook lieb_net.ipynb
```

As figuras são salvas automaticamente na pasta `Resultados/`.

---

# O que é a Rede de Lieb?

A Rede de Lieb é uma rede quadrada com três sítios por célula unitária, de dois tipos: o do vértice, chamado **A**, e os das arestas, chamados **B** ($\mathrm{B}_x$ e $\mathrm{B}_y$). A modelagem *tight-binding* é dada pelo Hamiltoniano:

$$
\mathcal{H} = \sum_i \epsilon_i c_i^\dagger c_i - t \sum_{\langle ij \rangle} \left(c_i^\dagger c_j + \text{H.c.}\right) - t' \sum_{\langle\langle ij \rangle\rangle} \left(c_i^\dagger c_j + \text{H.c.}\right)
$$

onde $\epsilon_i$ é a energia *on-site* do sítio $i$, $t$ é o *hopping* entre vizinhos (A–B) e $t'$ é o *hopping* entre próximos vizinhos (B–B).

Os parâmetros utilizados são:

| Parâmetro | Valor |
|---|---|
| Distância entre sítios A | $a = 2,6$ nm |
| Unidade de energia | $\|t\|$ |
| Energias *on-site* | $\varepsilon_A = -\Delta/2$ e $\varepsilon_B = \Delta/2$, com $\Delta \in \{0, \|t\|\}$ |
| *Hopping* de próximos vizinhos | $t' \in \{0,\ t/\sqrt{2}\}$ (hipótese: $t \propto 1/d$) |
| Caminho na Zona de Brillouin | $\Gamma - X - M - \Gamma$ |

Os quatro casos estudados são:

| Caso | Energias *on-site* | *Hopping* $t'$ |
|---|---|---|
| (a) | iguais ($\Delta = 0$) | nulo |
| (b) | diferentes ($\Delta = \|t\|$) | nulo |
| (c) | iguais ($\Delta = 0$) | $t/\sqrt{2}$ |
| (d) | diferentes ($\Delta = \|t\|$) | $t/\sqrt{2}$ |

---

# Principais resultados

- **Banda plana:** para $t' = 0$, a banda 2 é plana em $E = \varepsilon_B$ para qualquer $\Delta$, com peso apenas nos sítios B, o que corresponde a estados localizados.
- **Cone de Dirac:** para $\Delta = 0$, as bandas se tocam em um cone de Dirac no ponto $M$.
- **Energias *on-site* diferentes:** abrem um *gap* de energia $\Delta$ em $M$, e a banda plana acompanha $\varepsilon_B$.
- ***Hopping* de próximos vizinhos:** quebra a planicidade da banda 2, que permanece plana apenas ao longo de $X - M$, alarga as bandas e deixa a DOS assimétrica, sem alterar o *gap* em $M$.
- **Ocupação** (com $E_F = 0$ e $k_BT = 0,1\,\|t\|$): os casos com $\Delta = 0$ são metálicos, enquanto os casos com $\Delta = \|t\|$ têm *gap*, com excitação térmica para a banda 2 apreciável apenas no caso (b).

A discussão completa está no [relatório](https://drive.google.com/file/d/1Lb_1Nb8_d7JD7JUFMyoYbta2rVem9Y2B/view?usp=sharing).

---

# Referências

1. M. R. Slot *et al.* "Experimental realization and characterization of an electronic Lieb lattice". *Nature Physics* 13.7 (jul. de 2017), pp. 672–676.
2. PythTB Developers. *Python Tight Binding (PythTB) Documentation*. https://pythtb.readthedocs.io/en/latest/.
3. D. Leykam, A. Andreanov e S. Flach. "Artificial flat band systems: from lattice models to experiments". *Advances in Physics: X* 3.1 (2018), p. 1473052.

---

# Professor orientador

<table>
  <tr>
    <td align="center">
      <a href="https://bv.fapesp.br/pt/pesquisador/709013/felipe-david-crasto-de-lima/">
        <img src="https://pages.cnpem.br/cepidcemol/wp-content/uploads/sites/201/2026/02/Felipe-Crasto-1000x1000.jpg" width="100px;" alt="Foto do Felipe no site do CNPEM"/><br>
        <b>Prof. Dr. Felipe David Crasto de Lima</b>
      </a>
    </td>
  </tr>
</table>

---

# Autor

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/Giulio-Roux">
        <img src="https://avatars.githubusercontent.com/u/208799014?v=4" width="100px;" alt="Foto do Giulio no Github"/><br>
        <b>Giulio Oertel Spinelli Roux César</b>
      </a>
    </td>
  </tr>
</table>
