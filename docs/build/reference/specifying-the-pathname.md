---
title: Especificar la ruta de acceso
ms.date: 11/04/2016
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
ms.openlocfilehash: 07afcd102b2b1839b3925ad1e6905507ea316361
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423331"
---
# <a name="specifying-the-pathname"></a>Especificar la ruta de acceso

Cada opción de archivo de salida acepta un *pathname* argumento que se puede especificar una ubicación y un nombre para el archivo de salida. El argumento puede incluir un nombre de la unidad, el directorio y el nombre de archivo. Se permite ningún espacio entre la opción y el argumento.

Si *pathname* incluye un nombre de archivo sin extensión, el compilador emite la salida de una extensión predeterminada. Si *pathname* incluye un directorio, pero ningún nombre de archivo, el compilador crea un archivo con un nombre predeterminado en el directorio especificado. El nombre predeterminado se basa en el nombre base del archivo de código fuente y una extensión predeterminada según el tipo del archivo de salida. Si se deja *pathname* por completo, el compilador crea un archivo con un nombre predeterminado en un directorio predeterminado.

Como alternativa, el *pathname* argumento puede ser un nombre de dispositivo (AUX, CON, NUL o PRN) en lugar de un nombre de archivo. No use un espacio entre la opción y el nombre del dispositivo o un signo de dos puntos como parte del nombre del dispositivo.

|Nombre del dispositivo|Representa|
|-----------------|----------------|
|AUX|Dispositivo auxiliar|
|CON|Consola|
|PRN|Impresora|
|NUL|Dispositivo nulo (no se crea ningún archivo)|

## <a name="example"></a>Ejemplo

La línea de comandos siguiente envía un archivo de asignaciones a la impresora:

```
CL /FmPRN HELLO.CPP
```

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](../../build/reference/output-file-f-options.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
