---
title: "__super | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__super_cpp"
  - "__super"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__super (palabra clave) [C++]"
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __super
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Permite establecer explícitamente que se está llamando a una implementación de la clase base para una función que se va a reemplazar.  
  
## Sintaxis  
  
```  
  
__super::  
member_function  
();  
  
```  
  
## Comentarios  
 Todos los métodos accesibles de la clase base se consideran durante la fase de la resolución de sobrecarga y la función que proporciona la mejor coincidencia es la que se llama.  
  
 `__super` solo puede aparecer en el cuerpo de una función miembro.  
  
 `__super` no se puede utilizar con una declaración using.  Vea [using \(declaración\)](../cpp/using-declaration.md) para obtener más información.  
  
 Con la introducción de [atributos](../windows/cpp-attributes-reference.md) que insertan código, el código podría contener una o más clases base cuyos nombres puede no conocer, pero que contienen métodos a los que desea llamar.  
  
## Ejemplo  
  
```  
// deriv_super.cpp  
// compile with: /c  
struct B1 {  
   void mf(int) {}  
};  
  
struct B2 {  
   void mf(short) {}  
  
   void mf(char) {}  
};  
  
struct D : B1, B2 {  
   void mf(short) {  
      __super::mf(1);   // Calls B1::mf(int)  
      __super::mf('s');   // Calls B2::mf(char)  
   }  
};  
```  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)