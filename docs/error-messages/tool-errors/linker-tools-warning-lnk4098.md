---
title: Las herramientas del vinculador LNK4098 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4098
dev_langs:
- C++
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2068534d51ae1350510a349f875c1977299edb1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019162"
---
# <a name="linker-tools-warning-lnk4098"></a>Advertencia de las herramientas del vinculador LNK4098

DEFAULTLIB entra en conflicto 'library' con el uso de otras bibliotecas; Use/NODEFAULTLIB: biblioteca

Está intentando vincular con bibliotecas incompatibles.

> [!NOTE]
>  Ahora, las bibliotecas en tiempo de ejecución contienen directivas para evitar mezclar distintos tipos. Recibirá esta advertencia si se intenta usar diferentes tipos o de depuración y las versiones que no sean de depuración de la biblioteca en tiempo de ejecución en el mismo programa. Por ejemplo, si se compila un archivo para usar una biblioteca de tipo de tiempo de ejecución y otro archivo para usar otro tipo (por ejemplo, el único subproceso y multiproceso) e intenta vincularlos, obtendrá esta advertencia. Se deben compilar todos los archivos de código fuente para usar la misma biblioteca de tiempo de ejecución. Consulte la [utilizar la biblioteca en tiempo de ejecución](../../build/reference/md-mt-ld-use-run-time-library.md) (**/MD**, **/MT**, **/LD**) opciones del compilador para obtener más información.

Puede usar el enlazador [/verbose: lib](../../build/reference/verbose-print-progress-messages.md) modificador para determinar qué bibliotecas busca el vinculador. Si recibe LNK4098 y desea volver a crear un archivo ejecutable que usa, por ejemplo, el único subproceso, las bibliotecas en tiempo de ejecución que no sean de depuración, use el **/verbose: lib** opción para averiguar qué bibliotecas busca el vinculador. El vinculador debe mostrar LIBC.lib y no LIBCMT.lib, MSVCRT.lib, LIBCD.lib, LIBCMTD.lib o MSVCRTD.lib como las bibliotecas de búsqueda. Puede indicar al enlazador que omita las bibliotecas en tiempo de ejecución incorrectas mediante el uso de [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) para cada biblioteca que desea omitir.

La siguiente tabla muestra qué bibliotecas deben omitirse según la biblioteca de tiempo de ejecución que desee usar.

|Para usar esta biblioteca en tiempo de ejecución|Omitir estas bibliotecas|
|-----------------------------------|----------------------------|
|Un único subproceso (libc.lib)|LIBCMT.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|
|Multiproceso (libcmt.lib)|libc.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|
|Multiproceso con DLL (msvcrt.lib)|libc.lib, libcmt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|
|Depurar un único subproceso (libcd.lib)|libc.lib, libcmt.lib, msvcrt.lib, msvcrtd.lib, libcmtd.lib|
|Depuración multiproceso (libcmtd.lib)|libc.lib, libcmt.lib, msvcrt.lib, msvcrtd.lib, libcd.lib|
|Depuración multiproceso con DLL (msvcrtd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib|

Por ejemplo, si ha recibido esta advertencia y desea crear un archivo ejecutable que usa la versión de no depuración, un único subproceso de las bibliotecas en tiempo de ejecución, podía usar las siguientes opciones con el vinculador:

```
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```