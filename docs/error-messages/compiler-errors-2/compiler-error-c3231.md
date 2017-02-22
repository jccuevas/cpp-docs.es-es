---
title: "Error del compilador C3231 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3231"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3231"
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3231
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'arg' : el argumento de tipo de plantilla no puede utilizar un parámetro de tipo genérico  
  
 Las instancias de las plantillas se crean en tiempo de compilación, mientras que las instancias de los genéricos se crean en tiempo de ejecución.  Por consiguiente, no es posible generar código genérico que pueda llamar a la plantilla, puesto que no se pueden crear instancias de la plantilla en tiempo de ejecución, cuando por fin se conoce el tipo genérico.  
  
 El código siguiente genera el error C3231:  
  
```  
// C3231.cpp  
// compile with: /clr /LD  
template <class T> class A;  
  
generic <class T>  
ref class C {  
   void f() {  
      A<T> a;   // C3231  
   }  
};  
```