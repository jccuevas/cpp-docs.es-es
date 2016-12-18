---
title: "Advertencia del compilador (nivel 3) C4290 | Microsoft Docs"
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
  - "C4290"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4290"
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 3) C4290
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se ha omitido la especificación de excepciones de C\+\+, excepto para indicar que una función no es \_\_declspec\(nothrow\)  
  
 Una función se ha declarado con la especificación de excepciones, que Visual C\+\+ admite pero no implementa.  Puede que sea necesario volver a compilar y vincular código que contenga especificaciones de excepción omitidas durante la compilación, para que pueda reutilizarse en futuras versiones que admitan las especificaciones de excepción.  
  
 Para obtener más información, vea [Especificaciones de excepciones \(throw\)](../../cpp/exception-specifications-throw-cpp.md).  
  
 Se puede evitar esta advertencia mediante la directiva pragma [warning](../../preprocessor/warning.md):  
  
```  
#pragma warning( disable : 4290 )  
```  
  
 El ejemplo de código siguiente genera el error C4290:  
  
```  
// C4290.cpp  
// compile with: /EHs /W3 /c  
void f1(void) throw(int) {}   // C4290  
  
// OK  
void f2(void) throw() {}  
void f3(void) throw(...) {}  
```