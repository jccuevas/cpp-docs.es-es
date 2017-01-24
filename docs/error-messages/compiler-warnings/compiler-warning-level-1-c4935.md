---
title: "Advertencia del compilador (nivel 1) C4935 | Microsoft Docs"
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
  - "C4935"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4935"
ms.assetid: a36c56d3-571a-44dd-bb0f-bcc6b020e134
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4935
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

especificador de acceso de ensamblado modificado desde 'access'  
  
 Se modificó la visibilidad del ensamblado de un tipo. El compilador usa el último especificador que encuentra. Por ejemplo, la visibilidad del ensamblado de una declaración adelantada puede ser diferente de la visibilidad del ensamblado de la definición de clase.  
  
 El error C4935 solo se puede alcanzar con **\/clr:oldSyntax**.  
  
 El ejemplo siguiente genera la advertencia C4935:  
  
```  
// C4935.cpp // compile with: /clr:oldSyntax /W1 /c public __gc public class X {   // C4935 int i; };  
```