---
title: Advertencia de las herramientas del vinculador LNK4210
ms.date: 11/04/2016
f1_keywords:
- LNK4210
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
ms.openlocfilehash: 75376129ce0033c717a4da3074cee9de132d357d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816274"
---
# <a name="linker-tools-warning-lnk4210"></a>Advertencia de las herramientas del vinculador LNK4210

> sección *sección* existe; se puede ser no controlada terminadores o inicializadores estáticos

## <a name="remarks"></a>Comentarios

Algo de código ha introducido terminadores o inicializadores estáticos, pero no se ejecuta el código de inicio de la biblioteca de VCRuntime o su equivalente (lo que necesita para ejecutar los terminadores o inicializadores estáticos) cuando se inicia la aplicación. Estos son algunos ejemplos de código que requiere terminadores o inicializadores estáticos:

- Variable de clase global con un constructor, destructor o tabla de funciones virtuales.

- Inicializado con una constante de tiempo de compilación que no es una variable global.

Para corregir este problema, pruebe uno de los siguientes:

- Quite todo el código con inicializadores estáticos.

- No use [/NOENTRY](../../build/reference/noentry-no-entry-point.md). Después de quitar/NOENTRY, también es posible que deba quitar [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) desde la línea de comandos del vinculador.

- Si la compilación usa/MT, agregue libcmt.lib, libvcruntime.lib y libucrt.lib a la línea de comandos del vinculador. Si la compilación usa/MTd, agregue libcmtd.lib, vcruntimed.lib y libucrtd.lib.

- Al pasar de/CLR: compilación puro a/CLR, quite el [/Entry](../../build/reference/entry-entry-point-symbol.md) opción desde la línea del vinculador. Esto permite la inicialización de CRT e inicializadores estáticos que se ejecutará al iniciar la aplicación. El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

El [/GS](../../build/reference/gs-buffer-security-check.md) opción del compilador requiere inicialización mediante el `__security_init_cookie` función. Esta inicialización se proporciona de forma predeterminada en el código de inicio de biblioteca de VCRuntime que se ejecuta en `_DllMainCRTStartup`.

- Si el proyecto se compiló con/Entry y/Entry se pasa una función distinta `_DllMainCRTStartup`, debe llamar la función `_CRT_INIT` para inicializar la biblioteca CRT. Esta llamada por sí solo no es suficiente si el archivo DLL utiliza/GS, requiere a inicializadores estáticos o se llama en el contexto de código MFC o ATL. Consulte [Visual C++ y archivos DLL de comportamiento de la biblioteca de tiempo de ejecución](../../build/run-time-library-behavior.md) para obtener más información.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](../../build/reference/linking.md)
