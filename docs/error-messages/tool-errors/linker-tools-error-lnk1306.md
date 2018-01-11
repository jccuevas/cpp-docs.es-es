---
title: Las herramientas del vinculador LNK1306 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1306
dev_langs: C++
helpviewer_keywords: LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 32b6589fa5e4d7dc02ccb9a6c3157c109725b895
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1306"></a>Error de las herramientas del vinculador LNK1306  
  
> No se puede administrar la función de punto de entrada de archivo DLL; compilar a código nativo  
  
`DllMain`no se pueden compilar en MSIL; primero se debe compilar en código nativo.  
  
Para resolver este problema,  
  
-   Compilar el archivo que contiene el punto de entrada sin **/CLR**.  
  
-   Coloque el punto de entrada en un `#pragma unmanaged` sección.  
  
Para obtener más información, consulte:  
  
-   [/CLR (compilación de common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [managed, unmanaged](../../preprocessor/managed-unmanaged.md)  
  
-   [Inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md)  
  
-   [Archivos DLL y comportamiento de la biblioteca en tiempo de ejecución de Visual C++](../../build/run-time-library-behavior.md)  
  
## <a name="example"></a>Ejemplo  
  
El ejemplo siguiente genera el error LNK1306.  
  
```cpp  
// LNK1306.cpp  
// compile with: /clr /link /dll /entry:NewDllMain  
// LNK1306 error expected  
#include <windows.h>  
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {  
   return 1;  
}  
```  
  
Para corregir este problema, no use la opción/CLR compile este archivo, o usar un `#pragma` directiva para colocar la definición de punto de entrada en una sección no administrada como se muestra en este ejemplo:  
  
```cpp  
// LNK1306fix.cpp  
// compile with: /clr /link /dll /entry:NewDllMain  
#include <windows.h>  
#pragma managed(push, off)  
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {  
   return 1;  
}  
#pragma managed(pop)  
```  
