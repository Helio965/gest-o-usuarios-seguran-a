# Portfólio de Práticas de Gestão de Usuários e Segurança

Este repositório contém scripts e exemplos sobre práticas de gestão de usuários e segurança. As seções incluem:
- Gestão de Usuários
- Segurança da Informação
- Segurança em Aplicações Web

Pasta Gestao-de-Usuarios
Conteúdo exemplo:

gerenciamento_contas.py: Script para criar, modificar e excluir contas de usuários.

permissoes_grupos.py: Script para gerenciar permissões e grupos de usuários.

gerenciamento_contas.py

def criar_usuario(username, senha):
    
    # Função para criar um usuário
    
    print(f"Usuário {username} criado com sucesso.")
    
    # Adicione a lógica para criar um usuário

def modificar_usuario(username, nova_senha):
   
    # Função para modificar um usuário existente
    
    print(f"Usuário {username} modificado com sucesso.")
    
    # Adicione a lógica para modificar um usuário

def excluir_usuario(username):
   
    # Função para excluir um usuário
    
    print(f"Usuário {username} excluído com sucesso.")
    
    # Adicione a lógica para excluir um usuário

# Exemplo de uso
criar_usuario("novo_usuario", "senha123")
modificar_usuario("novo_usuario", "senha456")
excluir_usuario("novo_usuario")
permissoes_grupos.py

def criar_grupo(nome_grupo):
   
    # Função para criar um grupo
    
    print(f"Grupo {nome_grupo} criado com sucesso.")
   
    # Adicione a lógica para criar um grupo

def adicionar_usuario_ao_grupo(username, nome_grupo):
   
    # Função para adicionar um usuário a um grupo
   
    print(f"Usuário {username} adicionado ao grupo {nome_grupo}.")
   
    # Adicione a lógica para adicionar um usuário a um grupo

# Exemplo de uso
criar_grupo("admin")
adicionar_usuario_ao_grupo("usuario1", "admin")
Pasta Seguranca-da-Informacao
Conteúdo exemplo:

criptografia_dados.py: Script para criptografar e descriptografar dados.

controle_acesso.py: Script para gerenciar políticas de controle de acesso.

criptografia_dados.py

from cryptography.fernet import Fernet

# Geração de chave
def gerar_chave():
    
    chave = Fernet.generate_key()
    
    with open("chave.key", "wb") as chave_file:
       
        chave_file.write(chave)

# Criptografia de dados
def criptografar_dados(dados, chave):
  
    f = Fernet(chave)
   
    dados_criptografados = f.encrypt(dados.encode())
    
    return dados_criptografados

# Descriptografia de dados
def descriptografar_dados(dados_criptografados, chave):
   
    f = Fernet(chave)
    
    dados_descriptografados = f.decrypt(dados_criptografados).decode()
    
    return dados_descriptografados

# Exemplo de uso
gerar_chave()
with open("chave.key", "rb") as chave_file:
    chave = chave_file.read()

dados = "informação sensível"
dados_criptografados = criptografar_dados(dados, chave)
print(f"Dados criptografados: {dados_criptografados}")

dados_descriptografados = descriptografar_dados(dados_criptografados, chave)
print(f"Dados descriptografados: {dados_descriptografados}")
controle_acesso.py

def definir_politica_acesso(usuario, recurso, permissao):
   
    # Função para definir políticas de acesso
    
    print(f"Usuário {usuario} tem permissão {permissao} para o recurso {recurso}.")
    
    # Adicione a lógica para definir políticas de acesso

# Exemplo de uso
definir_politica_acesso("usuario1", "arquivo.txt", "leitura")
Pasta Seguranca-em-Aplicacoes-Web
Conteúdo exemplo:

prevenção_vulnerabilidades.py: Script para prevenir vulnerabilidades comuns.

desenvolvimento_seguro.py: Exemplo de código seguro.

prevenção_vulnerabilidades.py

from flask import Flask, request, render_template_string

app = Flask(__name__)

@app.route('/xss')
def xss():
   
    # Prevenção de XSS
   
    usuario_input = request.args.get('input', '')
    
    seguro_input = render_template_string('{{ input | e }}', input=usuario_input)
   
    return f'Input seguro: {seguro_input}'

@app.route('/sql')
def sql():
   
    # Exemplo simples de SQL Injection (não utilize em produção)
   
    user_id = request.args.get('user_id', '')
    
    # Prevenção usando consultas parametrizadas
   
    query = "SELECT * FROM usuarios WHERE id = %s"
   
    # Execute a consulta segura com o banco de dados

if __name__ == '__main__':
    app.run(debug=True)
desenvolvimento_seguro.py

def validar_entrada(input_usuario):
   
    # Exemplo de validação de entrada
    
    if isinstance(input_usuario, str) and len(input_usuario) < 100:
    
        return True
    
    return False

# Exemplo de uso

entrada = "<script>alert('XSS')</script>"

if validar_entrada(entrada):
   
    print("Entrada válida e segura.")

else:
  
    print("Entrada inválida ou insegura."
