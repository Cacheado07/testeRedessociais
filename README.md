# Documentação de Testes - Sistema de Rede Social

## Sumário de Casos de Teste

1. [Criar Usuário](#1-criar-usuário)
2. [Criar Postagem](#2-criar-postagem)
3. [Seguir Usuário](#3-seguir-usuário)
4. [Curtir Postagem](#4-curtir-postagem)
5. [Comentar em Postagem](#5-comentar-em-postagem)

---

### ======== 1 ponto ==============================

## 1. Criar Usuário

### Caso de Teste: `test_criar_usuario_valido` ✅
**Objetivo**: Verificar se o sistema cria um usuário com nome válido.  
**Entrada**: Nome do usuário: "Alice"  
**Saída Esperada**: Usuário criado com ID único, sem seguidores e sem usuários seguidos.

### Caso de Teste: `test_criar_usuario_nome_em_branco`✅
**Objetivo**: Verificar o comportamento do sistema ao tentar criar um usuário com o nome em branco.  
**Entrada**: Nome do usuário: ""  
**Saída Esperada**: Lançar um `IndexError`.

---

## 2. Criar Postagem

### Caso de Teste: `test_criar_postagem_valida` ✅
**Objetivo**: Verificar se uma postagem é criada corretamente para um usuário existente.  
**Entrada**: ID do usuário: 1, Texto: "Olá, mundo!"  
**Saída Esperada**: Postagem criada com ID único associada ao usuário 1, contendo o texto fornecido.

### Caso de Teste: `test_criar_postagem_texto_em_branco` ✅
**Objetivo**: Verificar o comportamento do sistema ao tentar criar uma postagem com texto em branco.  
**Entrada**: ID do usuário: 1, Texto: ""  
**Saída Esperada**: Lançar um `IndexError`.

### Caso de Teste: `test_criar_postagem_usuario_inexistente` ✅
**Objetivo**: Verificar o comportamento do sistema ao tentar criar uma postagem para um usuário inexistente.  
**Entrada**: ID do usuário: 999, Texto: "Postagem de usuário inexistente"  
**Saída Esperada**: Lançar um `IndexError`.

---

## 3. Seguir Usuário

### Caso de Teste: `test_seguir_usuario_valido` ✅
**Objetivo**: Verificar se um usuário pode seguir outro usuário existente.  
**Entrada**: ID do seguidor: 1, ID do usuário a seguir: 2  
**Saída Esperada**: Usuário 1 segue usuário 2, e o usuário 2 tem o usuário 1 como seguidor.

### Caso de Teste: `test_seguir_usuario_mesmo_usuario`
**Objetivo**: Verificar o comportamento ao tentar seguir a si mesmo.  
**Entrada**: ID do seguidor: 1, ID do usuário a seguir: 1  
**Saída Esperada**: Nenhuma ação de seguir é realizada; o usuário não deve seguir a si mesmo.

### Caso de Teste: `test_seguir_usuario_inexistente`
**Objetivo**: Verificar o comportamento ao tentar seguir um usuário inexistente.  
**Entrada**: ID do seguidor: 1, ID do usuário a seguir: 999  
**Saída Esperada**: Lançar um `IndexError`.

---

## 4. Curtir Postagem

### Caso de Teste: `test_curtir_postagem_valida` ✅
**Objetivo**: Verificar se um usuário pode curtir uma postagem existente.  
**Entrada**: ID do usuário: 1, ID da postagem: 1  
**Saída Esperada**: A postagem tem o usuário 1 como curtidor.

### Caso de Teste: `test_curtir_mesma_postagem_novamente`
**Objetivo**: Verificar se o sistema impede curtidas duplicadas na mesma postagem por um mesmo usuário.  
**Entrada**: ID do usuário: 1, ID da postagem: 1  
**Saída Esperada**: A postagem possui apenas uma curtida do usuário 1.

### Caso de Teste: `test_curtir_postagem_inexistente`
**Objetivo**: Verificar o comportamento ao tentar curtir uma postagem inexistente.  
**Entrada**: ID do usuário: 1, ID da postagem: 999  
**Saída Esperada**: Lançar um `IndexError`.

---

## 5. Comentar em Postagem

### Caso de Teste: `test_comentar_postagem_valida`
**Objetivo**: Verificar se um usuário pode comentar em uma postagem existente.  
**Entrada**: ID do usuário: 1, ID da postagem: 1, Texto do comentário: "Ótimo post!"  
**Saída Esperada**: Comentário adicionado à postagem 1 com o texto fornecido.

### Caso de Teste: `test_comentar_texto_em_branco`
**Objetivo**: Verificar o comportamento ao tentar comentar com texto em branco.  
**Entrada**: ID do usuário: 1, ID da postagem: 1, Texto do comentário: ""  
**Saída Esperada**: Lançar um `ValueError`.

### Caso de Teste: `test_comentar_postagem_inexistente`
**Objetivo**: Verificar o comportamento ao tentar comentar em uma postagem inexistente.  
**Entrada**: ID do usuário: 1, ID da postagem: 999, Texto do comentário: "Comentário"  
**Saída Esperada**: Lançar um `IndexError`.

### ============ 1 ponto ===========================

### Caso de Teste: `test_excluir_usuario` - valor 1pt
**Objetivo**: Verificar o comportamento ao excluir um usuario valido.  
**Entrada**: ID do usuário: 1  
**Saída Esperada**: Usuario excluido, postagens desse usuario excluidas, comentários e curtidas desse usuário excluídos.
