---
title: "Advertencia del compilador (nivel 1) C4674 | Microsoft Docs"
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
  - "C4674"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4674"
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4674
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'method' se debe declarar como 'static' y tener exactamente un parámetro  
  
 La firma de un operador de conversión no es correcta. El método no se considera una conversión definida por el usuario.  
  
 Al utilizar la nueva sintaxis \(**\/clr**\), consulte [Operadores definidos por el usuario](../../dotnet/user-defined-operators-cpp-cli.md) y [Conversiones definidas por el usuario](../../dotnet/user-defined-conversions-cpp-cli.md) para obtener información sobre la definición de operadores.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4674.  
  
```  
// C4674.cpp // compile with: /clr /WX /W1 /LD ref class G { int op_Implicit(int i) {   // C4674 return 0; } };  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4674.  
  
```  
// C4674_b.cpp // compile with: /clr:oldSyntax /W1 /LD __gc class G { int op_Implicit(int i) {   // C4674 // try the following line instead // static int op_Implicit(int i) { return 0; } };  
```