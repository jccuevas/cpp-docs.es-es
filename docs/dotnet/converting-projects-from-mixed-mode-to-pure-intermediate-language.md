---
title: Convertir proyectos de modo mixto a lenguaje intermedio puro
ms.date: 08/19/2019
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 8b22f3aaf706fa096f6c25ab8e9fdab6dc512cd8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208816"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>Convertir proyectos de modo mixto a lenguaje intermedio puro

Todos los C++ proyectos de Visual CLR se vinculan de forma predeterminada a las bibliotecas en tiempo de ejecución de C. Por consiguiente, estos proyectos se clasifican como aplicaciones de modo mixto, ya que combinan código nativo con código destinado al Common Language Runtime (código administrado). Cuando se compilan, se compilan en lenguaje intermedio (IL), también conocido como lenguaje intermedio de Microsoft (MSIL).

> [!IMPORTANT]
> Visual Studio 2015 en desuso y Visual Studio 2017 ya no admite la creación de código **/clr: Pure** o **/clr: Safe** para aplicaciones CLR. Si requiere ensamblados puros o seguros, se recomienda traducir la aplicación a C#.

Si usa una versión anterior del conjunto de herramientas del C++ compilador de Microsoft que admite **/clr: Pure** o **/clr: Safe**, puede usar este procedimiento para convertir el código en MSIL puro:

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>Para convertir la aplicación en modo mixto en lenguaje intermedio puro

1. Quitar vínculos a las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md) (CRT):

   1. En el archivo. cpp que define el punto de entrada de la aplicación, cambie el punto de entrada a `Main()`. El uso de `Main()` indica que el proyecto no se vincula a CRT.

   2. En Explorador de soluciones, haga clic con el botón secundario en el proyecto y seleccione **propiedades** en el menú contextual para abrir las páginas de propiedades de la aplicación.

   3. En la página de propiedades proyecto **avanzado** del **enlazador**, seleccione el **punto de entrada** y, a continuación, escriba **Main** en este campo.

   4. En el caso de las aplicaciones de consola, en la página de propiedades proyecto **del sistema** del **enlazador**, seleccione el campo **subsistema** y cámbielo a **consola (/Subsystem: Console)** .

      > [!NOTE]
      > No es necesario establecer esta propiedad para Windows Forms aplicaciones porque el campo **subsistema** está establecido en **Windows (/Subsystem: Windows)** de forma predeterminada.

   5. En *stdafx. h*, comente todas las instrucciones de `#include`. Por ejemplo, en las aplicaciones de consola:

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       O bien

       Por ejemplo, en Windows Forms aplicaciones:

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. En el caso de las aplicaciones Windows Forms, en Form1. cpp, comente la instrucción `#include` que hace referencia a Windows. h. Por ejemplo:

      ```cpp
      // #include <windows.h>
      ```

2. Agregue el código siguiente a *stdafx. h*:

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. Quitar todos los tipos no administrados:

   Siempre que sea necesario, reemplace los tipos no administrados por referencias a estructuras del espacio de nombres [System](/dotnet/api/system) . En la tabla siguiente se enumeran los tipos administrados comunes:

   |Estructura|Descripción|
   |---------------|-----------------|
   |[Boolean](/dotnet/api/system.boolean)|Representa un valor booleano.|
   |[Byte](/dotnet/api/system.byte)|Representa un entero de 8 bits sin signo.|
   |[Char](/dotnet/api/system.char)|Representa un carácter Unicode.|
   |[DateTime](/dotnet/api/system.datetime)|Representa un instante de tiempo, normalmente expresado en forma de fecha y hora del día.|
   |[Decimal](/dotnet/api/system.decimal)|Representa un número decimal.|
   |[Doble](/dotnet/api/system.double)|Representa un número de punto flotante de doble precisión.|
   |[GUID](/dotnet/api/system.guid)|Representa un identificador único global (GUID).|
   |[Int16](/dotnet/api/system.int16)|Representa un entero de 16 bits con signo.|
   |[Int32](/dotnet/api/system.int32)|Representa un entero de 32 bits con signo.|
   |[Int64](/dotnet/api/system.int64)|Representa un entero de 64 bits con signo.|
   |[IntPtr](/dotnet/api/system.intptr)|Tipo específico de la plataforma que se usa para representar un puntero o un identificador.|
   |[SByte](/dotnet/api/system.byte)|Representa un entero de 8 bits con signo.|
   |[Único](/dotnet/api/system.single)|Representa un número de punto flotante de precisión simple.|
   |[TimeSpan](/dotnet/api/system.timespan)|Representa un intervalo de tiempo.|
   |[UInt16](/dotnet/api/system.uint16)|Representa un entero de 16 bits sin signo.|
   |[UInt32](/dotnet/api/system.uint32)|Representa un entero de 32 bits sin signo.|
   |[UInt64](/dotnet/api/system.uint64)|Representa un entero de 64 bits sin signo.|
   |[UIntPtr](/dotnet/api/system.uintptr)|Tipo específico de la plataforma que se usa para representar un puntero o un identificador.|
   |[Hueco](/dotnet/api/system.void)|Indica un método que no devuelve un valor; es decir, el método tiene el tipo de valor devuelto void.|
