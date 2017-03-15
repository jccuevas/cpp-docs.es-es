---
title: "Error del compilador C2261 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2261"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2261"
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2261
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'cadena': la referencia de ensamblado no es válida y no puede resolverse  
  
 Un valor no era válido.  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> se utiliza para especificar un ensamblado de confianza.  Por ejemplo, si a.dll desea especificar b.dll como ensamblado de confianza, deberá especificar \(en a.dll\): InternalsVisibleTo\("b"\).  El motor en tiempo de ejecución permitirá entonces que b.dll tenga acceso a todo en a.dll \(excepto los tipos privados\).  
  
 Para obtener más información sobre la sintaxis correcta al especificar los ensamblados de confianza, vea [Ensamblados de confianza \(C\+\+\)](../../dotnet/friend-assemblies-cpp.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2261.  
  
```  
// C2261.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("a,a,a")];   // C2261  
[assembly: InternalsVisibleTo("a.a")];   // OK  
[assembly: InternalsVisibleTo("a")];   // OK  
```