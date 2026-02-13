# Organização de Computadores - Laboratório 1: Modelação de Sistemas e Profiling

Este repositório contém o código e os recursos desenvolvidos para o **1º Trabalho de Laboratório** da unidade curricular de **Organização de Computadores (LEIC)** no Instituto Superior Técnico (IST).

Os objetivos principais deste projeto são:
1.  Determinar as características das caches (L1 e L2) de um computador.
2.  Otimizar o desempenho de um algoritmo de multiplicação de matrizes utilizando conhecimentos sobre a hierarquia de memória.

## 📋 Descrição do Projeto

O projeto utiliza a biblioteca **PAPI (Performance Application Programming Interface)** para aceder aos contadores de hardware do processador, permitindo medir eventos como *cache misses*, ciclos de relógio e instruções executadas.

O trabalho está dividido em duas partes:
*   **Parte 1 (Modelação de Cache):** Utilização de micro-benchmarks (`cm1`) para inferir o tamanho, tamanho do bloco e associatividade das caches L1 e L2.
*   **Parte 2 (Otimização):** Análise e otimização da multiplicação de matrizes através de três implementações:
    *   `mm1`: Implementação ingénua (*Naïve*).
    *   `mm2`: Otimização com transposição de matriz (Melhoria da localidade espacial).
    *   `mm3`: Otimização com blocos (*Tiling* - Melhoria da localidade temporal).

## 💻 Especificações do Hardware (Target Platform)

Os testes foram realizados nos computadores do laboratório com as seguintes características (baseado no output de `lscpu`):

*   **CPU:** Intel(R) Core(TM) i5-7500 CPU @ 3.40GHz
*   **Arquitetura:** x86_64
*   **Caches:**
    *   L1 Data: 32 KiB (per core)
    *   L1 Instruction: 32 KiB (per core)
    *   L2: 256 KiB (per core)
    *   L3: 6 MiB (partilhada)
*   **Byte Order:** Little Endian

## 📂 Estrutura de Ficheiros

```text
.
├── cm1/                # Código para modelação da Cache (Cache Modeling)
│   ├── cm1.c           # Programa principal para teste de strides
│   ├── cm1_proc.sh     # Script para processamento de dados
│   └── Makefile
├── mm1/                # Multiplicação de Matrizes - Versão Base
│   ├── mm1.c           # Implementação i-j-k
│   └── Makefile
├── mm2/                # Multiplicação de Matrizes - Transposição
│   ├── mm2.c           # Implementação com matriz transposta
│   └── Makefile
├── mm3/                # Multiplicação de Matrizes - Tiling (Blocos)
│   ├── mm3.c           # Implementação otimizada com blocos
│   └── Makefile
