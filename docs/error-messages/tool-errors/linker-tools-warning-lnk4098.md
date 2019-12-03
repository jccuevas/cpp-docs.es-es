---
title: Advertencia de las herramientas del vinculador LNK4098
description: Describe cómo las bibliotecas incompatibles causan la advertencia de las herramientas del vinculador LNK4098 y cómo usar/NODEFAULTLIB para corregirlo.
ms.date: 12/02/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 9d0c7da0614651a98d5ed4f3bd3676c7d837ce67
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682942"
---
# <a name="linker-tools-warning-lnk4098"></a>Advertencia de las herramientas del vinculador LNK4098

> DEFAULTLIB '*Library*' está en conflicto con el uso de otras bibliotecas; usar/NODEFAULTLIB:*Library*

Está intentando vincular con bibliotecas no compatibles.

> [!NOTE]
> Las bibliotecas en tiempo de ejecución contienen ahora directivas para evitar la combinación de tipos diferentes. Recibirá esta advertencia si intenta usar tipos diferentes o versiones de depuración y no depuración de la biblioteca en tiempo de ejecución en el mismo programa. Por ejemplo, si compiló un archivo para usar un tipo de biblioteca en tiempo de ejecución y otro archivo para usar otro tipo (por ejemplo, depurar frente a comercial) e intentar vincularlos, recibirá esta advertencia. Debe compilar todos los archivos de código fuente para usar la misma biblioteca en tiempo de ejecución. Para obtener más información, vea las opciones del compilador [/MD,/MT,/LD (usar la biblioteca en tiempo de ejecución)](../../build/reference/md-mt-ld-use-run-time-library.md) .

Puede usar el modificador [/verbose: lib](../../build/reference/verbose-print-progress-messages.md) del vinculador para averiguar qué bibliotecas busca el enlazador. Por ejemplo, cuando el ejecutable utiliza las bibliotecas en tiempo de ejecución multiproceso y que no son de depuración, la lista indicada debe incluir LIBCMT. lib, no LIBCMTD. lib, MSVCRT. lib o MSVCRTD. lib. Puede indicar al enlazador que omita las bibliotecas en tiempo de ejecución incorrectas mediante [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) para cada biblioteca que desee omitir.

En la tabla siguiente se muestran las bibliotecas que deben omitirse en función de la biblioteca en tiempo de ejecución que desee usar. En la línea de comandos, use una opción **/NODEFAULTLIB** en cada biblioteca para omitir. En el IDE de Visual Studio, separe las bibliotecas que se van a omitir mediante punto y coma en la propiedad **omitir bibliotecas predeterminadas específicas** .

| Para usar esta biblioteca en tiempo de ejecución | Omitir estas bibliotecas |
|-----------------------------------|----------------------------|
| Multiproceso (libcmt. lib) | msvcrt. lib; libcmtd. lib; msvcrtd. lib |
| Multithreading mediante DLL (msvcrt. lib) | libcmt. lib; libcmtd. lib; msvcrtd. lib |
| Depuración multiproceso (libcmtd. lib) | libcmt. lib; msvcrt. lib; msvcrtd. lib |
| Depurar multiproceso mediante DLL (msvcrtd. lib) | libcmt. lib; msvcrt. lib; libcmtd. lib |

Por ejemplo, si ha recibido esta advertencia y desea crear un archivo ejecutable que use la versión de DLL que no sea de depuración de las bibliotecas en tiempo de ejecución, puede usar las siguientes opciones con el enlazador:

```cmd
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```
