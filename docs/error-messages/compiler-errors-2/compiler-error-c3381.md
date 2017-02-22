---
title: "Error del compilador C3381 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3381"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3381"
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3381
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'ensamblado' : los especificadores de acceso al ensamblado sólo están disponibles en el código compilado con la opción \/clr  
  
 Los tipos nativos son visibles fuera del ensamblado, pero sólo se puede especificar acceso de ensamblado para tipos nativos en una compilación **\/clr**.  
  
 Para obtener más información, vea [Visibilidad de tipos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) y [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3381.  
  
```  
// C3381.cpp  
// compile with: /c  
public class A {};   // C3381  
```