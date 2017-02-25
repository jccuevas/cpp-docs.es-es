---
title: "Error del compilador C3222 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3222"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3222"
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C3222
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parámetro': no se pueden declarar argumentos predeterminados para las funciones miembro de un tipo WinRT o administrado o funciones genéricas  
  
 No se permite declarar un parámetro de método con un argumento predeterminado.  Para resolver el problema, puede usarse una forma sobrecargada del método.  Es decir, defina un método con el mismo nombre pero sin parámetros y a continuación inicialice la variable en el cuerpo del método.  
  
 El código siguiente genera el error C3222:  
  
```  
// C3222_2.cpp  
// compile with: /clr  
public ref class G {  
   void f( int n = 0 );   // C3222  
};  
```  
  
 El código siguiente genera el error C3222:  
  
```  
// C3222.cpp  
// compile with: /clr:oldSyntax  
public __gc class G {  
   void f( int n = 0 );   // C3222  
};  
```