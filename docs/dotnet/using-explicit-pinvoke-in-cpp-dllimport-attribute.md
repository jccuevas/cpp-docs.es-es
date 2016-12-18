---
title: "Utilizar un elemento PInvoke expl&#237;cito en C++ (Atributo DllImport) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interoperabilidad de C++, invocación de plataforma"
  - "cálculo de referencias de datos [C++], invocación de plataforma"
  - "interoperabilidad [C++], invocación de plataforma"
  - "calcular las referencias [C++], invocación de plataforma"
  - "invocación de plataforma [C++], calcular las referencias en C++"
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar un elemento PInvoke expl&#237;cito en C++ (Atributo DllImport)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

.NET Framework proporciona características explícitas para invocación de plataforma \(PInvoke\) con el atributo `Dllimport` para permitir que las aplicaciones administradas llamen a funciones no administradas empaquetadas en archivos DLL.  La función PInvoke explícita se requiere en situaciones donde se empaquetan API no administradas como archivos DLL y el código fuente no está disponible.  Al llamar a las funciones de Win32, por ejemplo, se requiere PInvoke.  De lo contrario, utilice la función P\/Invoke implícita; vea [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md) para obtener más información.  
  
 PInvoke funciona utilizando <xref:System.Runtime.InteropServices.DllImportAttribute>.  Este atributo, que adopta el nombre del archivo DLL como primer argumento, se coloca delante de una declaración de función para cada punto de entrada de DLL que se vaya a utilizar.  La firma de la función debe corresponder al nombre de una función exportada por el archivo DLL \(aunque ciertas conversiones de tipos se pueden efectuar implícitamente definiendo las declaraciones `DllImport` en cuanto a tipos administrados\).  
  
 El resultado es un punto de entrada administrado para cada función de archivos DLL nativa que contiene el código de transición necesario \(o thunk\) y las conversiones de datos simples.  Las funciones administradas pueden efectuar entonces llamadas en el archivo DLL a través de estos puntos de entrada.  El código insertado en un módulo como resultado de PInvoke es administrado en su totalidad y se admite PInvoke para compilaciones con **\/clr**, **\/clr:pure** y **\/clr:safe**.  Para obtener más información, vea [Código puro y comprobable](../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## En esta sección  
  
-   [Llamar a funciones nativas desde código administrado](../dotnet/calling-native-functions-from-managed-code.md)  
  
-   [Cómo: Llamar a archivos DLL nativos desde el código administrado mediante PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)  
  
-   [Cómo: Calcular las referencias de cadenas mediante PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)  
  
-   [Cómo: Calcular las referencias a estructuras mediante PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
-   [Cómo: Calcular las referencias a matrices mediante PInvoke](../dotnet/how-to-marshal-arrays-using-pinvoke.md)  
  
-   [Cómo: Calcular las referencias de punteros a función mediante PInvoke](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)  
  
-   [Cómo: Calcular las referencias de punteros incrustados mediante PInvoke](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)  
  
## Vea también  
 [Llamar a funciones nativas desde código administrado](../dotnet/calling-native-functions-from-managed-code.md)