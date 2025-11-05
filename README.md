# Binary Search Tree en Java  
Estudiante: Julián Andrés Villa Alos – 396453

## Descripción del proyecto  
Este proyecto implementa un Árbol de Búsqueda Binaria (BST – *Binary Search Tree*) en Java, con los siguientes componentes:  
- Inserción de nodos  
- Búsqueda de valores  
- Recorridos: In-Order, Pre-Order y Post-Order  
- Eliminación (delete) de un nodo  

## Estructura del código  
El archivo principal es `BinarySearchTreeDemo.java`, que contiene dos clases internas:  
- **TreeNode**: representa cada nodo del árbol. Tiene un valor `int value`, referencias a `left`, `right` e `parent`.  
- **BinarySearchTree**: contiene la raíz `root` y los métodos para operar sobre el árbol.

### Operaciones implementadas  
**Insertar**  
- `insert(int newValue)`: si `root` es nulo, crea la raíz; de lo contrario llama a `insertNode(TreeNode current, int newValue)`.  
- `insertNode` compara `newValue` con `current.value`. Si es menor, va al hijo izquierdo; si es mayor, al hijo derecho. Si encuentra un espacio nulo lo inserta y fija el `parent`.

**Buscar**  
- `find(int target)`: llama a `findValue(TreeNode current, int target)`, que recorre recursivamente el árbol:  
  - Si `current` es nulo → no encontrado  
  - Si `current.value == target` → lo ha encontrado  
  - Si `target < current.value`, busca en `left`; sino en `right`.  

**Recorridos**  
- *In-Order*: `inorder()` imprime “Recorrido In-Order: ” y luego `inorderRec(root)` que recorre: izquierda → nodo → derecha.  
- *Pre-Order*: `preorder()` imprime “Recorrido Pre-Order: ” y luego `preorderRec(root)` que recorre: nodo → izquierda → derecha.  
- *Post-Order*: `postorder()` imprime “Recorrido Post-Order: ” y luego `postorderRec(root)` que recorre: izquierda → derecha → nodo.

**Eliminar (Delete)**  
- `delete(int value)`: llama a `deleteRec(TreeNode node, int value)`, que actúa recursivamente:  
  - Si `node` es nulo → retorno nulo  
  - Si `value < node.value` → va a `node.left = deleteRec(node.left, value)`  
  - Si `value > node.value` → va a `node.right = deleteRec(node.right, value)`  
  - Si `value == node.value` → encontró el nodo a eliminar:
    - Caso 1: sin hijos (`left == null` y `right == null`) → devuelve `null`, eliminando el nodo.  
    - Caso 2: un solo hijo (por ejemplo `left == null`) → devuelve `node.right` reemplazando al nodo.  
    - Caso 3: dos hijos → se encuentra el sucesor mínimo del sub-árbol derecho (`findMin(node.right)`), se copia su valor en el nodo actual, y luego se elimina ese sucesor en `node.right = deleteRec(node.right, minNode.value)`.  
- `findMin(TreeNode node)`: devuelve el nodo con el valor más pequeño en ese sub-árbol (el más izquierdo).  

## Cómo compilar y ejecutar  
1. Guarda `BinarySearchTreeDemo.java` en una carpeta local.  
2. Abre terminal/command prompt en esa carpeta.  
3. Compila:  
   ```bash
   javac BinarySearchTreeDemo.java
   java BinarySearchTreeDemo

