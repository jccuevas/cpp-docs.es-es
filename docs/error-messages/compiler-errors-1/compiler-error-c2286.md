---
title: "Error del compilador C2286 | Microsoft Docs"
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
  - "C2286"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2286"
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2286
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

los punteros a miembros de la representación 'identificador' ya están establecidos en 'inheritance'; se ha omitido la declaración  
  
 Una misma clase tiene dos representaciones distintas de puntero a miembros.  
  
 Para obtener más información, vea [Palabras clave de herencia](../../cpp/inheritance-keywords.md).  
  
## Ejemplo  
 El código siguiente genera el error C2286:  
  
```  
// C2286.cpp  
// compile with: /c  
class __single_inheritance X;  
class __multiple_inheritance X;   // C2286  
class  __multiple_inheritance Y;   // OK  
```