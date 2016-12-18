---
title: "Error del compilador C2004 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2004"
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se esperaba 'defined\(id\)'  
  
 Debe aparecer un identificador en los paréntesis que siguen a la palabra clave del preprocesador.  
  
 Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio. NET 2003: faltan paréntesis en la directiva del preprocesador. Si no existe paréntesis de cierre de una directiva de preprocesador, el compilador generará un error.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C2004:  
  
```  
// C2004.cpp // compile with: /DDEBUG #include <stdio.h> int main() { #if defined(DEBUG   // C2004 printf_s("DEBUG defined\n"); #endif }  
```  
  
## Ejemplo  
 Posible solución:  
  
```  
// C2004b.cpp // compile with: /DDEBUG #include <stdio.h> int main() { #if defined(DEBUG) printf_s("DEBUG defined\n"); #endif }  
```