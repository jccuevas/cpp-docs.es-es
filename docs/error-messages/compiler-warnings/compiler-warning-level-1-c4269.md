---
title: "Advertencia del compilador (nivel 1) C4269 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4269"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4269"
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4269
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : los datos automáticos de 'const' inicializados con el constructor predeterminado generado por el compilador proporcionan resultados no fiables  
  
 Una instancia automática **const** de una clase no trivial se inicializa con un constructor predeterminado generado por el compilador.  
  
## Ejemplo  
  
```  
// C4269.cpp  
// compile with: /c /LD /W1  
class X {  
public:  
   int m_data;  
};  
  
void g() {  
   const X x1;   // C4269  
};  
```  
  
 Dado que esta instancia de la clase se genera en la pila, el valor inicial de `m_data` puede ser cualquier cosa.  Asimismo, como se trata de una instancia **const**, el valor `m_data` nunca puede modificarse.