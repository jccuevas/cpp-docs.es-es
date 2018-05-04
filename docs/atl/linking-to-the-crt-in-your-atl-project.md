---
title: Vinculación a CRT en un proyecto ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- DllMainCRTStartup
- wWinMainCRTStartup
- WinMainCRTStartup
dev_langs:
- C++
helpviewer_keywords:
- CRT, linking with ATL
- WinMainCRTStartup method
- DllMainCRTStartup method
- wWinMainCRTStartup method
- ATL, C Run-Time library (CRT)
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec0d93f8770ebbd893491c0e8b8eed239396e00a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>Vinculación a CRT en un proyecto ATL
El [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md) (CRT) proporcionan muchas funciones útiles que pueden realizar programación mucho más fácil durante el desarrollo de ATL. Todos los proyectos ATL se vinculan a la biblioteca CRT. Puede ver las ventajas y desventajas de vinculación de método en [ventajas e inconvenientes del método que se utiliza para vincular a CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md).  
  
## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>Efectos de vinculación a CRT en la imagen del programa  
 Si se vinculan estáticamente a CRT, código de CRT se coloca en la imagen ejecutable y no debe tener el archivo DLL de CRT presente en un sistema para ejecutar la imagen. Si vincula dinámicamente a CRT, las referencias al código en el archivo DLL de CRT se colocan en la imagen, pero no el propio código. En el orden de la imagen para que se ejecute en un sistema determinado, el archivo DLL de CRT debe estar presente en el sistema. Incluso cuando vincula dinámicamente a CRT, es posible que parte del código se puede vincular estáticamente (por ejemplo, **DllMainCRTStartup**).  
  
 Al vincular la imagen, se explícita o implícitamente especifica un punto de entrada que el sistema operativo llamará a después de cargar la imagen. Para un archivo DLL, es el punto de entrada predeterminado **DllMainCRTStartup**. Para un archivo EXE, es **WinMainCRTStartup**. Puede invalidar el valor predeterminado con la opción de vinculador/ENTRY. La biblioteca CRT proporciona una implementación para **DllMainCRTStartup**, **WinMainCRTStartup**, y **wWinMainCRTStartup** (el punto de entrada Unicode para un archivo EXE). Estos puntos de entrada proporcionado por el CRT llamar a constructores de objetos globales e inicializar otras estructuras de datos que se utilizan algunas funciones de CRT. Este código de inicio agrega unos 25 KB a la imagen si está vinculada estáticamente. Si está vinculado dinámicamente, la mayoría del código está en el archivo DLL, por lo que el tamaño de la imagen seguirá siendo reducido.  
  
 Para obtener más información, vea el tema del vinculador [/ENTRY (símbolo de punto de entrada)](../build/reference/entry-entry-point-symbol.md).  
  
## <a name="optimization-options"></a>Opciones de optimización  
 Mediante la opción del vinculador/OPT: NOWIN98 puede reducir aún más control ATL predeterminado en unos 10 KB, a costa de aumentar la carga de tiempo en los sistemas de Windows 98. Para obtener más información sobre la vinculación de opciones, vea [especificación /OPT (optimizaciones)](../build/reference/opt-optimizations.md).  
  
## <a name="see-also"></a>Vea también  
 [Programar con ATL y el código de tiempo de ejecución de C](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Archivos DLL y comportamiento de la biblioteca en tiempo de ejecución de Visual C++](../build/run-time-library-behavior.md)

