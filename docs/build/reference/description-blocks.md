---
title: Bloques de descripción
description: NMAKE utiliza bloques de descripción para asociar destinos, dependencias y comandos en un archivo make.
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: e4e80b59d3d30b3b34c55b40d337ef5c078e6404
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322259"
---
# <a name="description-blocks"></a>Bloques de descripción

Los bloques de descripción forman el núcleo de un archivo make. Describen los *destinos*o archivos que se van a crear y sus *dependencias,* los archivos necesarios para crear los destinos. Un bloque de descripción puede incluir *comandos,* que describen cómo crear los destinos a partir de las dependencias. Un bloque de descripción es una línea de dependencia, opcionalmente seguida de un bloque de comandos:

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>Líneas de dependencia

Una línea de *dependencia* especifica uno o varios destinos y cero o más dependientes. Si un destino no existe o tiene una marca de tiempo anterior a una dependiente, NMAKE ejecuta los comandos en el bloque de comandos. NMAKE también ejecuta el bloque de comandos si el destino es un [pseudodestino.](pseudotargets.md) Este es un ejemplo de línea de dependencia:

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

En esta línea `hi_bye.exe` de dependencia, es el destino. Sus dependencias `hello.obj` `goodbye.obj`son `helper.lib`, , y . La línea de dependencia indica a `hello.obj`NMAKE que cree el destino cada vez que , `goodbye.obj`, o `helper.lib` que haya cambiado más recientemente que `hi_bye.exe`.

Un objetivo debe estar al principio de la línea. No se puede sangrar con espacios o pestañas. Utilice dos`:`puntos ( ) para separar los destinos de los dependientes. Se permiten espacios o pestañas entre`:`destinos, el separador de dos puntos ( ) y dependientes. Para dividir la línea de dependencia, utilice una barra diagonal inversa (`\`) después de un destino o dependiente.

Antes de ejecutar bloques de comandos, NMAKE examina todas las dependencias y las reglas de inferencia aplicables para crear un árbol de *dependencias.* Un árbol de dependencias especifica los pasos necesarios para actualizar completamente el destino. NMAKE comprueba recursivamente si un dependiente es en sí mismo un destino en otra lista de dependencias. Después de compilar el árbol de dependencias, NMAKE comprueba las marcas de tiempo. Si los dependientes del árbol son más recientes que el destino, NMAKE crea el destino.

## <a name="targets"></a><a name="targets"></a>Objetivos

La sección de destinos de una línea de dependencia especifica uno o varios destinos. Un destino puede ser cualquier nombre de archivo válido, nombre de directorio o [pseudodestino.](pseudotargets.md) Separe varios destinos mediante uno o varios espacios o pestañas. Los objetivos no distinguen mayúsculas de minúsculas. Las rutas de acceso se permiten con nombres de archivo. Un destino y su ruta de acceso no pueden superar los 256 caracteres. Si el destino que precede a los dos puntos es un solo carácter, utilice un espacio de separación. De lo contrario, NMAKE interpreta la combinación de letras y dos puntos como un especificador de unidad.

### <a name="multiple-targets"></a><a name="multiple-targets"></a>Múltiples objetivos

NMAKE evalúa varios destinos en una sola dependencia como si cada uno se especificara en un bloque de descripción independiente.

Por ejemplo, esta regla:

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

se evalúa como:

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a><a name="cumulative-dependencies"></a>Dependencias acumuladas

Las dependencias son acumulativas en un bloque de descripción, si se repite un destino.

Por ejemplo, este conjunto de reglas,

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

se evalúa como:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Cuando tiene varios destinos en varias líneas de dependencia en un único bloque de descripción, NMAKE los evalúa como si cada uno se especificara en un bloque de descripción independiente. Sin embargo, solo los destinos de la última línea de dependencia utilizan el bloque de comandos. NMAKE intenta usar una regla de inferencia para los demás destinos.

Por ejemplo, este conjunto de reglas,

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

se evalúa como:

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a><a name="targets-in-multiple-description-blocks"></a>Objetivos en varios bloques de descripción

Para actualizar un destino en más de un bloque de descripción mediante comandos diferentes, especifique dos dos puntos consecutivos (::) entre objetivos y dependientes.

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a><a name="dependency-side-effects"></a>Efectos secundarios de la dependencia

Puede especificar un destino con dos puntos (:) en dos líneas de dependencia en diferentes ubicaciones. Si los comandos aparecen después de solo una de las líneas, NMAKE interpreta las dependencias como si las líneas fueran adyacentes o combinadas. No invoca una regla de inferencia para la dependencia que no tiene comandos. En su lugar, NMAKE asume que las dependencias pertenecen a un bloque de descripción y ejecuta los comandos especificados con la otra dependencia. Considere este conjunto de reglas:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

se evalúa como:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Este efecto no se produce si`::`se utiliza un doble signo ( ). Por ejemplo, este conjunto de reglas:

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

se evalúa como:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a><a name="pseudotargets"></a>Pseudotargets

Un *pseudodestino* es una etiqueta utilizada en lugar de un nombre de archivo en una línea de dependencia. Se interpreta como un archivo que no existe, y también está desactualizado. NMAKE asume que la marca de tiempo de un pseudodestino es la misma que la más reciente de todos sus dependientes. Si no tiene dependientes, se asume la hora actual. Si se utiliza un pseudodestino como destino, sus comandos siempre se ejecutan. Un pseudodestino utilizado como dependiente también debe aparecer como destino en otra dependencia. Sin embargo, esa dependencia no necesita tener un bloque de comandos.

Los nombres de pseudodestino siguen las reglas de sintaxis de nombre de archivo para los destinos. Sin embargo, si el nombre no tiene una extensión, puede superar el límite de 8 caracteres para los nombres de archivo y puede tener hasta 256 caracteres.

Los pseudodestinos son útiles cuando se desea que NMAKE cree más de un destino automáticamente. NMAKE solo genera los destinos especificados en la línea de comandos. O bien, si no se especifica ningún destino de línea de comandos, solo compila el primer destino de la primera dependencia del archivo make. Puede indicar a NMAKE que cree varios destinos sin enumerarlos individualmente en la línea de comandos. Escriba un bloque de descripción con una dependencia que contenga un pseudodestino y enumere los destinos que desea crear como sus dependientes. A continuación, coloque este bloque de descripción primero en el archivo make o especifique el pseudodestino en la línea de comandos NMAKE.

En este ejemplo, UPDATE es un pseudodestino.

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

Cuando se evalúa UPDATE, NMAKE copia todos los archivos del directorio actual en la unidad y el directorio especificados.

En el siguiente archivo makefile, el `all` pseudodestino se compila y `project1.exe` `project2.exe` si se especifica uno `all` o ningún destino en la línea de comandos. El pseudodestino `setenv` cambia la variable `.exe` de entorno LIB antes de que se actualicen los archivos:

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a><a name="dependents"></a>Dependientes

En una línea de dependencia, especifique cero`:`o más dependientes después de los dos puntos ( ) o dos puntos (`::`), utilizando cualquier nombre de archivo válido o [pseudodestino](pseudotargets.md). Separe varios dependientes mediante uno o varios espacios o pestañas. Los dependientes no distinguen mayúsculas de minúsculas. Las rutas de acceso se permiten con nombres de archivo.

### <a name="inferred-dependents"></a><a name="inferred-dependents"></a>Dependientes inferidos

Junto con los dependientes que enumera explícitamente en la línea de dependencia, NMAKE puede asumir un *dependiente deducido.* Un dependiente deducido se deriva de una regla de inferencia y se evalúa antes que los dependientes explícitos. Cuando un dependiente deducido está desactualizado en comparación con su destino, NMAKE invoca el bloque de comandos para la dependencia. Si un dependiente inferido no existe o está desactualizado en comparación con sus propios dependientes, NMAKE primero actualiza el dependiente inferido. Para obtener más información acerca de los dependientes inferidos, consulte Reglas de [inferencia](inference-rules.md).

### <a name="search-paths-for-dependents"></a><a name="search-paths-for-dependents"></a>Buscar rutas de búsqueda de dependientes

Puede especificar una ruta de búsqueda opcional para cada dependiente. Esta es la sintaxis para especificar un conjunto de directorios para buscar:

> **•**_directorio_\[**;** _directorio_...] **•**_dependiente_

Incluya los nombres de`{ }`directorio entre llaves ( ). Separe varios directorios con`;`un punto y coma ( ). No se permiten espacios ni pestañas. NMAKE busca el dependiente primero en el directorio actual y, a continuación, en la lista de directorios en el orden especificado. Puede utilizar una macro para especificar parte o la totalidad de una ruta de búsqueda. Solo el dependiente especificado utiliza esta ruta de búsqueda.

#### <a name="directory-search-path-example"></a>Ejemplo de ruta de búsqueda de directorios

Esta línea de dependencia muestra cómo crear una especificación de directorio para una búsqueda:

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

El `reverse.exe` destino tiene `retro.obj`uno dependiente, . La lista cerrada de llaves especifica dos directorios. NMAKE busca `retro.obj` primero en el directorio actual. Si no está allí, NMAKE `\src\omega` busca en `e:\repo\backwards` el directorio y, a continuación, en el directorio.

## <a name="see-also"></a>Consulte también

[Referencia de NMAKE](nmake-reference.md)
