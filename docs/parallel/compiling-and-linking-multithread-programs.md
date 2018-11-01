---
title: Compilar y vincular programas multiproceso
ms.date: 11/04/2016
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
ms.openlocfilehash: 3d98f5341de1374c9119e2a4303c94fcfb005e29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558891"
---
# <a name="compiling-and-linking-multithread-programs"></a>Compilar y vincular programas multiproceso

El programa Bounce.c se introdujo en [ejemplo programa multiproceso en C](sample-multithread-c-program.md).

Compilar programas multiproceso de forma predeterminada.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Para compilar y vincular el programa multiproceso Bounce.c desde dentro del entorno de desarrollo

1. En el menú **Archivo** , haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**.

1. En el **tipos de proyecto** panel, haga clic en **Win32**.

1. En el **plantillas** panel, haga clic en **aplicación de consola Win32**y, a continuación, denomine al proyecto.

1. Agregue el archivo que contiene el código fuente de C al proyecto.

1. En el **compilar** menú, compile el proyecto, haga clic en el **compilar** comando.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Para compilar y vincular el programa multiproceso Bounce.c desde la línea de comandos

1. Compile y vincule el programa:

    ```
    CL BOUNCE.C
    ```

## <a name="see-also"></a>Vea también

[Multithreading con C y Win32](multithreading-with-c-and-win32.md)