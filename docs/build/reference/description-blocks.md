---
title: Bloques de descripción
description: NMAKE usa bloques de descripción para asociar los destinos, las dependencias y los comandos en un archivo make.
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: fb9cf4400c96b588e8704e972dd29ab27f41cae9
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144522"
---
# <a name="description-blocks"></a>Bloques de descripción

Los bloques de Descripción forman el núcleo de un archivo make. Describen los *destinos*, o archivos que se van a crear, y sus *dependencias*, los archivos necesarios para crear los destinos. Un bloque de descripción puede incluir *comandos*, que describen cómo crear los destinos a partir de las dependencias. Un bloque de descripción es una línea de dependencia, seguido opcionalmente por un bloque de comandos:

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>Líneas de dependencia

Una *línea de dependencia* especifica uno o más destinos, y cero o más dependientes. Si un destino no existe o tiene una marca de tiempo anterior a un dependiente, NMAKE ejecuta los comandos en el bloque de comandos. NMAKE también ejecuta el bloque de comandos si el destino es un [pseudodestino](pseudotargets.md). A continuación se muestra una línea de dependencia de ejemplo:

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

En esta línea de dependencia, `hi_bye.exe` es el destino. Sus dependencias son `hello.obj`, `goodbye.obj`y `helper.lib`. La línea de dependencia indica a NMAKE que compile el destino cada vez que `hello.obj`, `goodbye.obj`o `helper.lib` ha cambiado más recientemente que `hi_bye.exe`.

Un destino debe estar al principio de la línea. No se puede aplicar sangría a los espacios ni a las tabulaciones. Use un signo de dos puntos (`:`) para separar los destinos de los dependientes. Se permiten espacios o tabulaciones entre los destinos, el separador de dos puntos (`:`) y los dependientes. Para dividir la línea de dependencia, use una barra diagonal inversa (`\`) después de un destino o dependiente.

Antes de ejecutar los bloques de comandos, NMAKE examina todas las dependencias y cualquier regla de inferencia aplicable para crear un *árbol de dependencias*. Un árbol de dependencia especifica los pasos necesarios para actualizar completamente el destino. NMAKE comprueba de forma recursiva si un dependiente es en sí mismo un destino en otra lista de dependencias. Después de compilar el árbol de dependencias, NMAKE comprueba las marcas de tiempo. Si los dependientes del árbol son más recientes que el destino, NMAKE crea el destino.

## <a name="targets"></a> Destinos

La sección de destinos de una línea de dependencia especifica uno o varios destinos. Un destino puede ser cualquier nombre de archivo, nombre de directorio o [pseudodestino](pseudotargets.md)válidos. Separe varios destinos mediante el uso de uno o varios espacios o tabulaciones. Los destinos no distinguen mayúsculas de minúsculas. Se permiten rutas de acceso con nombres de archivo. Un destino y su ruta de acceso no pueden superar los 256 caracteres. Si el destino que va delante del signo de dos puntos es un carácter único, use un espacio de separación. De lo contrario, NMAKE interpreta la combinación de letras dos puntos como un especificador de unidad.

### <a name="multiple-targets"></a>Varios destinos

NMAKE evalúa varios destinos en una sola dependencia como si se hubieran especificado en un bloque de Descripción independiente.

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

### <a name="cumulative-dependencies"></a>Dependencias acumulativas

Las dependencias son acumulativas en un bloque de descripción, si un destino se repite.

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

Cuando hay varios destinos en varias líneas de dependencia en un solo bloque de descripción, NMAKE los evalúa como si se hubieran especificado en un bloque de Descripción independiente. Sin embargo, solo los destinos de la última línea de dependencia usan el bloque de comandos. NMAKE intenta utilizar una regla de inferencia para los otros destinos.

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

### <a name="targets-in-multiple-description-blocks"></a>Destinos en bloques de Descripción múltiples

Para actualizar un destino en más de un bloque de Descripción mediante comandos diferentes, especifique dos dos puntos consecutivos (::) entre destinos y dependientes.

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a>Efectos secundarios de dependencia

Puede especificar un destino con dos puntos (:) en dos líneas de dependencia en ubicaciones diferentes. Si los comandos aparecen después de solo una de las líneas, NMAKE interpreta las dependencias como si fueran adyacentes o combinadas. No invoca una regla de inferencia para la dependencia que no tiene comandos. En su lugar, NMAKE supone que las dependencias pertenecen a un bloque de Descripción y ejecuta los comandos especificados con la otra dependencia. Tenga en cuenta este conjunto de reglas:

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

Este efecto no se produce si se usa un signo de dos puntos (`::`). Por ejemplo, este conjunto de reglas:

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

### <a name="pseudotargets"></a>Pseudodestinos

Un *pseudodestino* es una etiqueta utilizada en lugar de un nombre de archivo en una línea de dependencia. Se interpreta como un archivo que no existe y, por tanto, no está actualizado. NMAKE supone que la marca de tiempo de un pseudodestino es la misma que la más reciente de todos sus elementos dependientes. Si no tiene dependientes, se supone la hora actual. Si se usa un pseudodestino como destino, siempre se ejecutan sus comandos. Un pseudodestino utilizado como dependiente también debe aparecer como un destino en otra dependencia. Sin embargo, esa dependencia no necesita tener un bloque de comandos.

Los nombres de pseudodestino siguen las reglas de sintaxis de nombre de archivo para los destinos. Sin embargo, si el nombre no tiene una extensión, puede superar el límite de 8 caracteres para los nombres de archivo y puede tener una longitud de hasta 256 caracteres.

Pseudodestinos son útiles cuando se desea que NMAKE compile más de un destino automáticamente. NMAKE solo compila los destinos especificados en la línea de comandos. O bien, si no se especifica ningún destino de línea de comandos, solo se genera el primer destino en la primera dependencia del archivo make. Puede indicar a NMAKE que cree varios destinos sin enumerarlos individualmente en la línea de comandos. Escriba un bloque de descripción con una dependencia que contenga un pseudodestino y enumere los destinos que desea compilar como dependientes. Después, coloque primero este bloque de descripción en el archivo make o especifique el pseudodestino en la línea de comandos de NMAKE.

En este ejemplo, la actualización es un pseudodestino.

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

Cuando se evalúa UPDATE, NMAKE copia todos los archivos del directorio actual en la unidad y el directorio especificados.

En el siguiente archivo make, el pseudodestino `all` compila `project1.exe` y `project2.exe` si `all` o no se especifica ningún destino en la línea de comandos. El pseudodestino `setenv` cambia la variable de entorno LIB antes de que se actualicen los archivos de `.exe`:

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a>Dependientes

En una línea de dependencia, especifique cero o más dependientes después del signo de dos puntos (`:`) o dos puntos dobles (`::`), con cualquier nombre de archivo o [pseudodestino](pseudotargets.md)válidos. Separe varios dependientes mediante el uso de uno o varios espacios o tabulaciones. Los elementos dependientes no distinguen mayúsculas de minúsculas. Se permiten rutas de acceso con nombres de archivo.

### <a name="inferred-dependents"></a>Dependientes inferidos

Junto con los dependientes que se enumeran explícitamente en la línea de dependencia, NMAKE puede suponer un *dependiente deducido*. Un dependiente deducido se deriva de una regla de inferencia y se evalúa antes que los dependientes explícitos. Cuando un dependiente deducido no está actualizado en comparación con su destino, NMAKE invoca el bloque de comandos para la dependencia. Si un dependiente deducido no existe o no está actualizado respecto a sus propios dependientes, NMAKE actualiza primero el dependiente deducido. Para obtener más información sobre los dependientes inferidos, vea [reglas de inferencia](inference-rules.md).

### <a name="search-paths-for-dependents"></a>Rutas de acceso de búsqueda para dependientes

Puede especificar una ruta de acceso de búsqueda opcional para cada dependiente. Esta es la sintaxis para especificar un conjunto de directorios para buscar:

> **{** _directorio_\[ **;** _directorio_...] **}** _dependiente_

Incluya los nombres de directorio entre llaves (`{ }`). Separe varios directorios con un punto y coma (`;`). No se permiten espacios ni pestañas. NMAKE busca primero el dependiente en el directorio actual y, a continuación, en la lista de directorios en el orden especificado. Puede usar una macro para especificar parte o la totalidad de una ruta de acceso de búsqueda. Solo el dependiente especificado usa esta ruta de acceso de búsqueda.

#### <a name="directory-search-path-example"></a>Ejemplo de ruta de búsqueda de directorio

Esta línea de dependencia muestra cómo crear una especificación de directorio para una búsqueda:

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

El `reverse.exe` de destino tiene un `retro.obj`dependiente. La lista entre llaves especifica dos directorios. NMAKE busca primero `retro.obj` en el directorio actual. Si no existe, NMAKE busca en el directorio de `\src\omega` y, a continuación, en el directorio de `e:\repo\backwards`.

## <a name="see-also"></a>Vea también

[Referencia de NMAKE](nmake-reference.md)
