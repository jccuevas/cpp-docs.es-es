---
title: Archivos de comandos de CL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1e2b25330bd326ac32dbe1c1b8abcc37c89d09
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894764"
---
# <a name="cl-command-files"></a>Archivos de comandos de CL

Un archivo de comandos es un archivo de texto que contiene las opciones y los nombres de archivo en caso contrario, escribiría en la [línea de comandos](../../build/reference/compiler-command-line-syntax.md) o especifique mediante la [variable de entorno de CL](../../build/reference/cl-environment-variables.md). CL acepta un archivo de comandos del compilador como un argumento en la variable de entorno de CL o en la línea de comandos. A diferencia de la línea de comandos o la variable de entorno de CL, un archivo de comandos permite utilizar varias líneas de opciones y nombres de archivo.

Opciones y nombres de archivo en un archivo de comandos, se procesan según la ubicación de un nombre de archivo de comandos dentro de la variable de entorno de CL o en la línea de comandos. Sin embargo, si la opción /link aparece en el archivo de comandos, todas las opciones en el resto de la línea se pasan al vinculador. Opciones de las líneas siguientes en el archivo de comandos y opciones en la línea de comandos después de la invocación del comando archivo todavía se aceptan como opciones del compilador. Para obtener más información sobre cómo afecta el orden de las opciones a su interpretación, vea [orden de las opciones de CL](../../build/reference/order-of-cl-options.md).

Un archivo de comandos no debe contener el comando CL. Cada opción debe comenzar y terminar en la misma línea; no se puede usar la barra diagonal inversa (**\\**) para combinar una opción entre dos líneas.

Un archivo de comandos especificado por un signo de arroba (**\@**) seguido por un nombre de archivo; el nombre de archivo puede especificar una ruta de acceso absoluta o relativa.

Por ejemplo, si es el siguiente comando en un archivo denominado RESP:

```  
/Og /link LIBC.LIB
```  

y especifique el siguiente comando de CL:

```  
CL /Ob2 @RESP MYAPP.C
```  

el comando de CL es como sigue:

```  
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```  

Tenga en cuenta que la línea de comandos y el archivo de comandos se combina eficazmente.

## <a name="see-also"></a>Vea también

[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
[opciones del compilador](../../build/reference/compiler-options.md)