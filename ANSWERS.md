# Checkpoint Questions

### 1. ¿Cuál es el valor predeterminado de flexDirection en React Native? ¿En qué se diferencia de CSS en la web?
En React Native, el valor predeterminado de `flexDirection` es `'column'`, por lo que los elementos hijos se apilan verticalmente. En cambio, en el CSS convencional para la web el valor por defecto es `row`, alineando los elementos de forma horizontal. Esta diferencia se adoptó intencionalmente porque las interfaces móviles están orientadas de manera vertical y los flujos de lectura y desplazamiento ocurren naturalmente de arriba hacia abajo.

### 2. ¿Cuál es la diferencia entre justifyContent y alignItems?
`justifyContent` se encarga de alinear y distribuir los elementos hijos a lo largo del eje principal (*main axis*), el cual en React Native es vertical por defecto. Por el contrario, `alignItems` determina la alineación a lo largo del eje transversal (*cross axis*), que corre de forma perpendicular al eje principal (horizontal por defecto). En conjunto, ambas propiedades permiten controlar con exactitud el posicionamiento y la distribución del espacio en las dos dimensiones del contenedor.

### 3. ¿Qué hace flex: 1 dentro de una fila (row)? ¿Y en el View más externo de una pantalla?
Dentro de una fila con `flexDirection: 'row'`, `flex: 1` permite que un elemento hijo se expanda horizontalmente para ocupar el espacio restante o dividirse el ancho equitativamente con otros componentes hermanos que también tengan `flex: 1`. En el `View` exterior de la pantalla, `flex: 1` hace que el contenedor abarque todo el alto y ancho visible del dispositivo. De esta forma se evita que la pantalla colapse a cero y se asegura que todo el contenido ocupe la vista completa.

### 4. ¿Cuál es la diferencia entre resizeMode="cover" y resizeMode="contain"?
`resizeMode="cover"` escala la imagen de manera uniforme para llenar todo el contenedor, recortando los bordes sobrantes en caso de que las proporciones de la imagen y del contenedor no coincidan. Por su parte, `resizeMode="contain"` escala la imagen uniformemente para que se muestre en su totalidad sin ningún tipo de recorte, lo que puede dejar franjas o espacios vacíos alrededor. En resumen, `cover` prioriza rellenar por completo el área visual, mientras que `contain` prioriza mostrar la imagen íntegra.

### 5. ¿Por qué usamos StyleSheet.create en lugar de objetos planos dentro del JSX?
`StyleSheet.create` valida las reglas y propiedades de estilo en tiempo de ejecución, lo que ayuda a detectar errores tipográficos o propiedades inválidas de forma temprana. Además, optimiza el rendimiento general de la app al registrar y cachear los estilos en el puente nativo mediante identificadores numéricos en lugar de recrear objetos nuevos en memoria en cada renderizado. Esto reduce la carga del recolector de basura y mantiene el código más organizado y legible.

### 6. ¿Por qué una sombra escrita con shadowColor no aparece en Android?
Las propiedades como `shadowColor`, `shadowOffset`, `shadowOpacity` y `shadowRadius` interactúan exclusivamente con las APIs de renderizado de iOS (Core Animation) y el motor de Android no las interpreta. En Android, las sombras se manejan mediante la propiedad nativa `elevation`, la cual se vincula directamente al sistema de elevación y profundidad de Material Design. Por ello, es necesario utilizar utilidades como `Platform.select` para configurar la propiedad correcta dependiendo del sistema operativo.