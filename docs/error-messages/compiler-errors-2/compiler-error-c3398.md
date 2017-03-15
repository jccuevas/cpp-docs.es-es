---
title: "Error del compilador C3398 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3398"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3398"
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3398
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador': no se puede convertir de 'signatura\_de\_función' a 'puntero\_a\_función'. La expresión de origen debe ser un símbolo de función  
  
 Si no se especifica la convención de llamada [\_\_clrcall](../../cpp/clrcall.md) cuando se compila con **\/clr**, el compilador genera dos puntos de entrada \(direcciones\) para cada función, un punto de entrada nativo y un punto de entrada administrado.  
  
 De forma predeterminada, el compilador devuelve el punto de entrada nativo, pero hay algunos casos en los que se desea el punto de entrada administrado \(por ejemplo, al asignar la dirección a un puntero a función `__clrcall`\). Para que el compilador elija correctamente el punto de entrada administrado en una asignación, el lado derecho debe ser un símbolo de función.