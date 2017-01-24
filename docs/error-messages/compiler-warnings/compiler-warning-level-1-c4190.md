---
title: "Advertencia del compilador (nivel 1) C4190 | Microsoft Docs"
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
  - "C4190"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4190"
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4190
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador1' tiene una vinculación C especificada, pero devuelve el tipo definido por el usuario 'identificador2' que es incompatible con C  
  
 Una función o un puntero a función poseen un tipo definido por el usuario, que es un tipo de clase, estructura, enumeración, unión o [\_\_value](../../misc/value.md) como tipo de valor devuelto y vinculación `extern` "C".  Esto se permite si:  
  
-   Todas las llamadas a esta función tienen lugar desde C\+\+.  
  
-   La definición de la función se realiza en C\+\+.  
  
## Ejemplo  
  
```  
// C4190.cpp  
// compile with: /W1 /LD  
struct X  
{  
   int i;  
   X ();  
   virtual ~X ();  
};  
  
extern "C" X func ();   // C4190  
```