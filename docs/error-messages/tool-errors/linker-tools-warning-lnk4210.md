---
title: Las herramientas del vinculador LNK4210 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4210
dev_langs:
- C++
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2bd34866264fdfea71ba7496ad9c94446fd5726
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4210"></a>Advertencia de las herramientas del vinculador LNK4210  
  
> sección *sección* existe; se puede tratamiento terminadores o inicializadores estáticos  
  
Parte del código ha introducido inicializadores o terminadores estáticos, pero el código de inicio de la biblioteca de VCRuntime o su equivalente (que debe ejecutar los terminadores o inicializadores estáticos) no se ejecuta cuando se inicia la aplicación. Estos son algunos ejemplos de código que requiere terminadores o inicializadores estáticos:  
  
-   Variable de clase global con un constructor, un destructor o una tabla de funciones virtuales.  
  
-   Variable global inicializada con una constante sin tiempo de compilación.  
  
Para corregir este problema, pruebe uno de los siguientes:  
  
-   Quite todo el código con inicializadores estáticos.  
  
-   No utilice [/NOENTRY](../../build/reference/noentry-no-entry-point.md). Después de quitar/NOENTRY, también tendrá que quitar [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) desde la línea de comandos del vinculador.  
  
-   Si la compilación usa/MT, agregar libcmt.lib, libvcruntime.lib y libucrt.lib a la línea de comandos del vinculador. Si la compilación usa/MTd, agregue libcmtd.lib, vcruntimed.lib y libucrtd.lib.  
  
-   Al mover de/CLR: pure compilación a/CLR, quite el [/Entry](../../build/reference/entry-entry-point-symbol.md) opción desde la línea del vinculador. Esto habilita la inicialización de CRT y permite inicializadores estáticos que se ejecutará en el inicio de la aplicación.  
  
 El [/GS](../../build/reference/gs-buffer-security-check.md) opción del compilador requiere inicialización que se realiza el `__security_init_cookie` función. Esta inicialización se proporciona de forma predeterminada en el código de inicio de biblioteca de VCRuntime que se ejecuta en `_DllMainCRTStartup`.  
  
-   Si el proyecto se compila con/Entry y/Entry se pasa una función distinta de `_DllMainCRTStartup`, debe llamar la función `_CRT_INIT` para inicializar la biblioteca CRT. Esta llamada por sí solo no es suficiente si el archivo DLL utiliza/GS, requiere a inicializadores estáticos o se llama en el contexto del código MFC o ATL. Vea [archivos DLL y Visual C++ comportamiento de la biblioteca de tiempo de ejecución](../../build/run-time-library-behavior.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)