---
title: Archivos de comandos de CL
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 1dc2d6bffe4d0681a04b875383215a0bbfc1a720
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440266"
---
# <a name="cl-command-files"></a>Archivos de comandos de CL

Un archivo de comandos es un archivo de texto que contiene opciones y nombres de archivo que, de lo contrario, escribiría en la [línea de comandos](compiler-command-line-syntax.md) o especificaría mediante la variable de [entorno de cl](cl-environment-variables.md). CL acepta un archivo de comandos del compilador como argumento en la variable de entorno de CL o en la línea de comandos. A diferencia de la línea de comandos o la variable de entorno de CL, un archivo de comandos permite utilizar varias líneas de opciones y nombres de archivo.

Las opciones y los nombres de archivo de un archivo de comandos se procesan según la ubicación de un nombre de archivo de comando dentro de la variable de entorno de CL o en la línea de comandos. Sin embargo, si la opción/Link aparece en el archivo de comandos, todas las opciones del resto de la línea se pasan al enlazador. Las opciones de las líneas siguientes del archivo de comandos y las opciones de la línea de comandos después de la invocación del archivo de comandos se siguen aceptando como opciones del compilador. Para obtener más información sobre cómo afecta el orden de las opciones a su interpretación, vea [orden de las opciones de cl](order-of-cl-options.md).

Un archivo de comandos no debe contener el comando CL. Cada opción debe comenzar y finalizar en la misma línea; no puede utilizar la barra diagonal inversa ( **\\** ) para combinar una opción en dos líneas.

Un archivo de comandos se especifica mediante un signo de arroba ( **\@** ) seguido de un nombre de archivo; el nombre de archivo puede especificar una ruta de acceso absoluta o relativa.

Por ejemplo, si el siguiente comando se encuentra en un archivo denominado RESP:

```
/Og /link LIBC.LIB
```

y especifica el siguiente comando de CL:

```
CL /Ob2 @RESP MYAPP.C
```

el comando para CL es el siguiente:

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

Tenga en cuenta que la línea de comandos y los comandos del archivo de comandos se combinan eficazmente.

## <a name="see-also"></a>Consulte también

[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)
