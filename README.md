# Blender Procedural Object Generator Operator

Este repositório contém um script em Python para o **Blender** que registra um operador customizado (`bpy.types.Operator`). Ao ser executado, o operador gera um cubo deformado proceduralmente com modificadores e aplica um material com iluminação de emissão (*Shader Nodes*).

---

## Funcionalidades

- **Criação de Geometria:** Adiciona um cubo primitivo à cena.
- **Transformação:** Aplica uma rotação no eixo X em $45^\circ$.
- **Subdivisão:** Aplica um modificador *Subdivision Surface* (Subsurf) de nível 3 e ativa o *Shade Smooth*.
- **Deslocamento Procedural (Displacement):** Adiciona um modificador *Displace* acoplado a uma textura do tipo `DISTORTED_NOISE`.
- **Propriedade Ajustável:** Expõe o parâmetro `noise_scale` via `FloatProperty`, permitindo ajustar a escala do ruído de 0.0 a 2.0.
- **Material de Emissão:** Cria um material baseado em nós (*Nodes*) utilizando o nó *Emission* com cor azul elétrico e alta intensidade.

---

## Como Usar

### Execução Direta via Text Editor

1. Abra o Blender.
2. Mude para a área de trabalho **Scripting** ou abra a janela do **Text Editor**.
3. Crie um novo texto (`New`), cole o código Python e clique no botão **Run Script** (ou pressione `Alt + P`).
4. O operador será registrado e executado imediatamente na cena 3D.

### Execução via Busca de Operadores

Após rodar o script uma vez, o operador estará registrado na sessão atual:

1. Pressione `F3` na **3D Viewport**.
2. Procure por **My Operator**.
3. Pressione `Enter` para executar.
4. Ajuste a propriedade **Noise Scale** no menu *Adjust Last Operation* (canto inferior esquerdo da tela).

---

## Estrutura da Classe do Operador

```python
class MyOperator(bpy.types.Operator):
    bl_idname = "object.my_operator"
    bl_label = "My Operator"
    bl_options = {'REGISTER', 'UNDO'}
