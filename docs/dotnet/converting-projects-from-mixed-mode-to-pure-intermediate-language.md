---
title: Convertir proyectos de modo mixto al lenguaje intermedio puro | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0276d5b5420ed0294b2cf3438190f79d03585744
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>Convertir proyectos de modo mixto a lenguaje intermedio puro
Todos los proyectos de Visual C++ CLR vinculan a las bibliotecas de tiempo de ejecución de C de forma predeterminada. Por lo tanto, estos proyectos se clasifican como aplicaciones en modo mixto, ya que combinan código nativo con código que tenga como destino common language runtime (código administrado). Cuando se compilan, sino que se compilan en lenguaje intermedio (IL), también conocido como lenguaje intermedio de Microsoft (MSIL).  
  
### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>Para convertir la aplicación de modo mixto a lenguaje intermedio puro  
  
1.  Quitar los vínculos a la [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md) (CRT):  
  
    1.  En el archivo .cpp que define el punto de entrada de la aplicación, cambiar el punto de entrada a `Main()`. Usar `Main()` indica que el proyecto no se vincula a la biblioteca CRT.  
  
    2.  En el Explorador de soluciones, haga clic en el proyecto y seleccione **propiedades** en el menú contextual para abrir las páginas de propiedades de la aplicación.  
  
    3.  En el **avanzadas** página de propiedades de proyecto para la **vinculador**, seleccione la **punto de entrada** y, a continuación, escriba **Main** en este campo.  
  
    4.  Para aplicaciones de consola, en la **System** página de propiedades de proyecto para la **vinculador**, seleccione la **subsistema** del campo y cambiar este valor a **consola (/ SUBSYSTEM:Console)**.  
  
        > [!NOTE]
        >  No es necesario establecer esta propiedad para aplicaciones de Windows Forms porque el **subsistema** campo está establecido en **Windows (/ SUBSYSTEM: WINDOWS)** de forma predeterminada.  
  
    5.  En stdafx.h, convierta en comentario todas las `#include` instrucciones. Por ejemplo, en las aplicaciones de consola:  
  
        ```  
        // #include <iostream>  
        // #include <tchar.h>  
        ```  
  
         O bien  
  
         Por ejemplo, en aplicaciones de Windows Forms:  
  
        ```  
        // #include <stdlib.h>  
        // #include <malloc.h>  
        // #include <memory.h>  
        // #include <tchar.h>  
        ```  
  
    6.  Para las aplicaciones de Windows Forms, en Form1.cpp, marque como comentario el `#include` instrucción que hace referencia a windows.h. Por ejemplo:  
  
        ```  
        // #include <windows.h>  
        ```  
  
2.  En stdafx.h, agregue el código siguiente:  
  
    ```  
    #ifndef __FLTUSED__  
    #define __FLTUSED__  
       extern "C" __declspec(selectany) int _fltused=1;  
    #endif  
    ```  
  
3.  Quitar todos los tipos no administrados:  
  
    1.  Donde sea necesario, reemplace los tipos no administrados por referencias a estructuras de la [System](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx) espacio de nombres. Tipos administrados más comunes se enumeran en la tabla siguiente:  
  
        |Estructura|Descripción|  
        |---------------|-----------------|  
        |[Boolean](https://msdn.microsoft.com/en-us/library/system.boolean\(v=vs.140\).aspx)|Representa un valor booleano.|  
        |[Byte](https://msdn.microsoft.com/en-us/library/system.byte\(v=vs.140\).aspx)|Representa un entero de 8 bits sin signo.|  
        |[Char](https://msdn.microsoft.com/en-us/library/system.char\(v=vs.140\).aspx)|Representa un carácter Unicode.|  
        |[DateTime](https://msdn.microsoft.com/en-us/library/system.datetime.datetime.aspx)|Representa un instante de tiempo, normalmente expresado en forma de fecha y hora del día.|  
        |[Decimal](https://msdn.microsoft.com/en-us/library/system.decimal\(v=vs.140\).aspx)|Representa un número decimal.|  
        |[Double](https://msdn.microsoft.com/en-us/library/system.double\(v=vs.140\).aspx)|Representa un número de punto flotante de precisión doble.|  
        |[GUID](https://msdn.microsoft.com/en-us/library/system.guid\(v=vs.140\).aspx)|Representa un identificador único global (GUID).|  
        |[Int16](https://msdn.microsoft.com/en-us/library/system.int16\(v=vs.140\).aspx)|Representa un entero de 16 bits con signo.|  
        |[Int32](https://msdn.microsoft.com/en-us/library/system.int32\(v=vs.140\).aspx)|Representa un entero de 32 bits con signo.|  
        |[Int64](https://msdn.microsoft.com/en-us/library/system.int64\(v=vs.140\).aspx)|Representa un entero de 64 bits con signo.|  
        |[IntPtr](https://msdn.microsoft.com/en-us/library/system.intptr\(v=vs.140\).aspx)|Tipo específico de la plataforma que se usa para representar un puntero o un identificador.|  
        |[SByte](https://msdn.microsoft.com/en-us/library/system.byte.aspx)|Representa un entero con signo de 8 bits.|  
        |[Single](https://msdn.microsoft.com/en-us/library/system.single.aspx)|Representa un número de punto flotante de precisión sencilla.|  
        |[TimeSpan](https://msdn.microsoft.com/en-us/library/system.timespan\(v=vs.140\).aspx)|Representa un intervalo de tiempo.|  
        |[UInt16](https://msdn.microsoft.com/en-us/library/system.uint16\(v=vs.140\).aspx)|Representa un entero de 16 bits sin signo.|  
        |[UInt32](https://msdn.microsoft.com/en-us/library/system.uint32\(v=vs.140\).aspx)|Representa un entero de 32 bits sin signo.|  
        |[UInt64](https://msdn.microsoft.com/en-us/library/system.uint64\(v=vs.140\).aspx)|Representa un entero de 64 bits sin signo.|  
        |[UIntPtr](https://msdn.microsoft.com/en-us/library/system.uintptr\(v=vs.140\).aspx)|Tipo específico de la plataforma que se usa para representar un puntero o un identificador.|  
        |[Void](https://msdn.microsoft.com/en-us/library/system.void\(v=vs.140\).aspx)|Indica un método que no devuelve un valor; es decir, el método tiene el tipo de valor devuelto void.|