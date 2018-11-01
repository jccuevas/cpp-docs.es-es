---
title: Sintaxis de la línea de comandos del vinculador
ms.date: 11/04/2016
helpviewer_keywords:
- linker [C++], syntax
- linker command line [C++]
- LINK tool [C++], command-line syntax
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
ms.openlocfilehash: 844d2fe4c02e274cda02fe71303f0b6dd092b431
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464121"
---
# <a name="linker-command-line-syntax"></a>Sintaxis de la línea de comandos del vinculador

Para ejecutar el vínculo. EXE, use la siguiente sintaxis de comando:

```
LINK arguments
```

El `arguments` incluyen opciones y los nombres de archivo y puede especificarse en cualquier orden. Las opciones son procesa primero y, a continuación, los archivos. Utilice uno o más espacios o tabulaciones para separar los argumentos.

> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de Visual Studio. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

En la línea de comandos, una opción consta de un especificador de opción, un guión (-) o una barra diagonal (/), seguido del nombre de la opción. Los nombres de opción no pueden abreviarse. Algunas opciones toman un argumento, especificado después de dos puntos (:). No se permiten espacios ni tabulaciones dentro de una especificación de opción, excepto dentro de una cadena entre comillas en la opción/Comment. Especifique los argumentos numéricos en notación de lenguaje de C o decimal. Los nombres de opción y sus argumentos de la palabra clave o nombre de archivo no distinguen mayúsculas de minúsculas, pero los identificadores como argumentos distinguen mayúsculas de minúsculas.

Para pasar un archivo al vinculador, especifique el nombre de archivo en la línea de comandos después del comando de vínculo. Puede especificar una ruta de acceso absoluta o relativa con el nombre de archivo, y puede usar caracteres comodín en el nombre de archivo. Si se omiten el punto (.) y la extensión de nombre de archivo, vínculo supone .obj con el fin de encontrar el archivo. VÍNCULO no usa extensiones de nombre de archivo o la falta de ellos para realizar suposiciones sobre el contenido de los archivos; Determina el tipo de archivo mediante el examen de él y lo procesa en consecuencia.

Link.exe devuelve cero si es correcto (sin errores).  En caso contrario, devuelve el número de error que detuvo el vínculo.  Por ejemplo, si el vinculador genera LNK1104, el vinculador devuelve 1104.  En consecuencia, el número más bajo de error devuelto en un error por el enlazador es 1000.  Un valor devuelto de 128 representa un problema de configuración con el sistema operativo o un archivo .config; no cargó el cargador de link.exe o c2.dll.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)