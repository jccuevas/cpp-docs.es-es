---
title: "Error de las herramientas del vinculador LNK1306 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1306"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1306"
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1306
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el punto de entrada del archivo DLL no se puede administrar; compilar a código nativo  
  
 DllMain no se puede compilar en MSIL; se debe compilar en código nativo.  
  
 Para resolverlo:  
  
-   Compile el archivo que contiene el punto de entrada sin **\/clr**.  
  
-   Coloque el punto de entrada en una sección `#pragma unmanaged`.  
  
-   Para obtener más información, vea  
  
-   [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [managed, unmanaged](../../preprocessor/managed-unmanaged.md)  
  
-   [Inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md)  
  
-   [Comportamiento de la biblioteca en tiempo de ejecución](../../build/run-time-library-behavior.md)  
  
## Ejemplo  
 El ejemplo siguiente genera el error LNK1306.  
  
```  
// LNK1306.cpp  
// compile with: /clr /link /dll /entry:NewDllMain  
// LNK1306 error expected  
#include <windows.h>  
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {  
   return 1;  
}  
```