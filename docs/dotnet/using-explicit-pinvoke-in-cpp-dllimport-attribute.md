---
title: Uso de PInvoke explícito en C++ (atributo DllImport) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 82215e4815d25dd116cf930be9cc0f40da761bf8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169509"
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>Utilizar un elemento PInvoke explícito en C++ (Atributo DllImport)
.NET Framework proporciona características explícitas para invocación de plataforma (PInvoke) con el atributo `Dllimport` para permitir que las aplicaciones administradas llamen a funciones no administradas empaquetadas en archivos DLL. La función PInvoke explícita se requiere en situaciones donde se empaquetan API no administradas como archivos DLL y el código fuente no está disponible. Al llamar a las funciones de Win32, por ejemplo, se requiere PInvoke. En caso contrario, utilice P implícita {Invoke; vea [uso de la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md) para obtener más información.  
  
 PInvoke funciona utilizando <xref:System.Runtime.InteropServices.DllImportAttribute>. Este atributo, que adopta el nombre del archivo DLL como primer argumento, se coloca delante de una declaración de función para cada punto de entrada de DLL que se vaya a utilizar. La firma de la función debe corresponder al nombre de una función exportada por el archivo DLL (aunque ciertas conversiones de tipos se pueden efectuar implícitamente definiendo las declaraciones `DllImport` en cuanto a tipos administrados).  
  
 El resultado es un punto de entrada administrado para cada función de archivos DLL nativa que contiene el código de transición necesario (o thunk) y las conversiones de datos simples. Las funciones administradas pueden efectuar entonces llamadas en el archivo DLL a través de estos puntos de entrada. El código insertado en un módulo como resultado de PInvoke es administrado en su totalidad.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Llamar a funciones nativas desde código administrado](../dotnet/calling-native-functions-from-managed-code.md)  
  
-   [Cómo: Llamar a archivos DLL nativos desde el código administrado mediante PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)  
  
-   [Cómo: Serializar cadenas mediante PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)  
  
-   [Cómo: Serializar estructuras mediante PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
-   [Cómo: Serializar matrices mediante PInvoke](../dotnet/how-to-marshal-arrays-using-pinvoke.md)  
  
-   [Cómo: Serializar punteros a función mediante PInvoke](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)  
  
-   [Cómo: Serializar punteros insertados mediante PInvoke](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)  
  
## <a name="see-also"></a>Vea también  
 [Llamar a funciones nativas desde código administrado](../dotnet/calling-native-functions-from-managed-code.md)