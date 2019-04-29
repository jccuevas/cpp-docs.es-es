---
title: Vinculación a CRT en un proyecto ATL
ms.date: 11/04/2016
helpviewer_keywords:
- CRT, linking with ATL
- WinMainCRTStartup method
- DllMainCRTStartup method
- wWinMainCRTStartup method
- ATL, C Run-Time library (CRT)
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
ms.openlocfilehash: e247897f42eea5b4ced5bc40b556137a1a5cd228
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261935"
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>Vinculación a CRT en un proyecto ATL

El [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md) (CRT) proporcionan muchas funciones útiles que pueden facilitar la programación mucho durante el desarrollo de ATL. Todos los proyectos ATL se vinculan a la biblioteca CRT. Puede ver las ventajas y desventajas de vinculación método [ventajas e inconvenientes de que el método que se utiliza para vincular a CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md).

## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>Efectos de vinculación a CRT en la imagen del programa

Si vincula estáticamente a CRT, código de CRT se coloca en la imagen ejecutable y no es necesario tener presente la DLL de CRT en un sistema para ejecutar la imagen. Si vincula dinámicamente a CRT, las referencias al código en el archivo DLL de CRT se colocan en la imagen, pero no el propio código. En el orden de la imagen que se ejecutará en un sistema determinado, el archivo DLL de CRT debe estar presente en el sistema. Incluso cuando vincula dinámicamente a CRT, es posible que parte del código se puede vincular estáticamente (por ejemplo, `DllMainCRTStartup`).

Al vincular la imagen, ya sea explícitamente o implícitamente especifique un punto de entrada que el sistema operativo llamará a después de cargar la imagen. Para un archivo DLL, es el punto de entrada predeterminado `DllMainCRTStartup`. Para un archivo EXE, resulta `WinMainCRTStartup`. Puede invalidar el valor predeterminado con la opción de vinculador/ENTRY. El CRT ofrece una implementación para `DllMainCRTStartup`, `WinMainCRTStartup`, y `wWinMainCRTStartup` (el punto de entrada Unicode para un archivo EXE). Estos puntos de entrada proporcionado CRT llamar a constructores de objetos globales e inicializar otras estructuras de datos que se usan algunas funciones de CRT. Este código de inicio agrega unos 25 KB a la imagen si está vinculada estáticamente. Si está vinculada dinámicamente, la mayoría del código está en el archivo DLL, por lo que se mantiene el tamaño de la imagen pequeño.

Para obtener más información, vea el tema del vinculador [/Entry (símbolo de punto de entrada)](../build/reference/entry-entry-point-symbol.md).

## <a name="optimization-options"></a>Opciones de optimización

Con la opción del vinculador/OPT: NOWIN98 puede reducir aún más control ATL predeterminado por 10 K, a costa de aumentar el tiempo en sistemas Windows 98 de carga. Para obtener más información sobre opciones de vinculación, consulte [/OPT (optimizaciones)](../build/reference/opt-optimizations.md).

## <a name="see-also"></a>Vea también

[Programar con ATL y código en tiempo de ejecución de C](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Archivos DLL y comportamiento de la biblioteca en tiempo de ejecución de Visual C++](../build/run-time-library-behavior.md)
