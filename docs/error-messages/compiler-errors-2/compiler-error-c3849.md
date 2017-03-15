---
title: "Error del compilador C3849 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3849"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3849"
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3849
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la llamada de estilo de función de una expresión de tipo 'tipo' perdería los calificadores const y volatile de todas las sobrecargas de operador número disponibles  
  
 Una variable con un tipo const o volatile especificado sólo puede llamar a funciones miembro definidas con calificaciones const o volatile iguales o superiores.  
  
 Para corregir este error, proporcione una función miembro adecuada.  No se puede ejecutar una conversión en un objeto calificado como const o volatile si dicha conversión implica la pérdida de calificación.  En una conversión se pueden ganar calificadores, pero no perderlos.  
  
 Los ejemplos siguientes generan el error C3849:  
  
```  
// C3849.cpp  
void glbFunc3(int i, char c)  
{  
   i;  
}  
typedef void (* pFunc3)(int, char);  
  
void glbFunc2(int i)  
{  
   i;  
}  
  
typedef void (* pFunc2)(int);  
  
void glbFunc1()  
{  
}  
typedef void (* pFunc1)();  
  
struct S4  
{  
   operator ()(int i)  
   {  
      i;  
   }  
  
   operator pFunc1() const  
   {  
      return &glbFunc1;  
   }  
  
   operator pFunc2() volatile  
   {  
      return &glbFunc2;  
   }  
  
   operator pFunc3()  
   {  
      return &glbFunc3;  
   }  
  
   // operator pFunc1() const volatile  
   // {  
   //    return &glbFunc1;  
   // }  
};  
  
int main()  
{  
   // Cannot call any of the 4 overloads of "operator ()(.....)" and   
   // "operator pFunc()" because none is declared as "const volatile"  
   const volatile S4 s4;  // can only call cv member functions of S4  
   s4();   // C3849 to resolve, uncomment member function  
}  
```