---
title: "Error del compilador C2062 | Microsoft Docs"
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
  - "C2062"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2062"
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2062
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

tipo 'tipo' inesperado  
  
 El compilador no esperaba un nombre de tipo.  
  
 El código siguiente genera el error C2062:  
  
```  
// C2062.cpp  
// compile with: /c  
struct A {  : int l; };   // C2062  
struct B { private: int l; };   // OK  
```  
  
 El error C2062 también puede producirse debido a la manera en que el compilador controla los tipos indefinidos en la lista de parámetros de un constructor.  Si el compilador encuentra un tipo indefinido \(o mal escrito\), da por supuesto que el constructor es una expresión y emite el error C2062.  Para resolverlo, utilice sólo tipos definidos en la lista de parámetro de un constructor.