# Bitácora de incidentes

## 1. Borrado accidental
- Qué pasó: Se borró el archivo docs/acuerdos.md por accidente desde el explorador.
- Comando que usamos: git restore docs/acuerdos.md
- Resultado: El archivo se recuperó tal como estaba en el último commit.

## 2. El cambio que nadie pidió
- Qué pasó: Se agregó el texto "Esto no va" al inicio de README.md sin que se hubiera pedido.
- Comando que usamos: git diff (para ver el cambio) y luego git restore README.md
- Resultado: El README volvió a su versión original, sin el texto agregado.

## 3. El add equivocado
- Qué pasó: Se creó un archivo de prueba borrador.txt y se agregó por error al staging con git add .
- Comando que usamos: git restore --staged borrador.txt, y luego se borró el archivo del disco con del borrador.txt
- Resultado: El archivo salió del staging sin quedar en el historial, y luego se eliminó del sistema.

## 4. La auditoría
- Qué pasó: Se necesitaba saber quién había escrito docs/acuerdos.md y cuándo.
- Comando que usamos: git log --pretty=format:"%h | %an | %ar" docs/acuerdos.md y git show --stat <hash>
- Resultado: Se confirmó que el commit fue de Brayan Steven Angel, con detalle del archivo y las líneas modificadas.

## Pregunta para pensar
¿Por qué git restore no puede recuperar un archivo que nunca se agregó con git add ni se confirmó con commit?

Porque git restore solo puede traer de vuelta versiones que Git ya tiene guardadas — ya sea en el staging o en algún commit del historial. Si un archivo nunca pasó por git add, Git nunca llegó a "conocerlo" ni a guardar una copia de su contenido en ningún lado. No hay ninguna versión anterior a la que Git pueda devolverte, porque para Git ese archivo simplemente no existía todavía.