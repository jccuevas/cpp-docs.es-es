---
title: "Error del compilador C2518 | Microsoft Docs"
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
  - "C2518"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2518"
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2518
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la palabra clave 'palabra clave' no es válida en la lista de clases base; se ha omitido  
  
 Las palabras clave `class` y `struct` no deben aparecer en una lista de clases base.  
  
 El código siguiente genera el error C2518:  
  
```  
// C2518.cpp  
// compile with: /c  
class B {};  
class C : public class B {};   // C2518  
class D: public B {};   // OK  
```