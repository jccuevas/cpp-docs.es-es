---
title: "Error del compilador C2057 | Microsoft Docs"
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
  - "C2057"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2057"
ms.assetid: 038a99d6-1f5a-42fa-8449-03b4ff11ee0b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2057
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se esperaba una expresión constante  
  
 El contexto exige una expresión constante, una expresión cuyo valor se conoce en tiempo de compilación.  
  
 El compilador debe conocer el tamaño de un tipo en tiempo de compilación para poder asignar espacio para una instancia de ese tipo.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2057 y muestra cómo corregirlo:  
  
```  
// C2057.cpp  
int i;  
int b[i];   // C2057 - value of i is unknown at compile time  
int main() {  
   const int i = 8;  
   int b[i]; // OK - value of i is fixed and known to compiler  
}  
```  
  
## Ejemplo  
 C tiene reglas más restrictivas para las expresiones de constante.  El ejemplo siguiente genera el error C2057 y muestra cómo corregirlo:  
  
```  
// C2057b.c  
#define ArraySize1 10  
int main() {   
   const int ArraySize2 = 10;   
   int h[ArraySize2];   // C2057 - C does not allow variables here  
   int h[ArraySize1];   // OK - uses preprocessor constant  
}  
```