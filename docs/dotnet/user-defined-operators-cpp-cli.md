---
title: "Operadores definidos por el usuario (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operadores definidos por el usuario bajo /clr"
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores definidos por el usuario (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se permite operadores definidos por el usuario para los tipos administrados como miembros estáticos o miembros de instancia, o en el ámbito global.  Sin embargo, solo los operadores estáticos son accesibles a través de metadatos a los clientes que se escriben en un lenguaje distinto de Visual C\+\+.  
  
 En un tipo de referencia, uno de los parámetros de un operador definido por el usuario estático debe ser uno de los siguientes:  
  
-   Un identificador \(^ de`type` \) a una instancia del tipo envolvente.  
  
-   Un direccionamiento indirecto de tipo de referencia \(^& o el type^% de`type`\) a un identificador a una instancia del tipo envolvente.  
  
 En un tipo de valor, uno de los parámetros de un operador definido por el usuario estático debe ser uno de los siguientes:  
  
-   Del mismo tipo que el tipo de valor que agrega.  
  
-   Un direccionamiento indirecto del tipo de puntero \(^ de`type`\) al tipo envolvente.  
  
-   Un direccionamiento indirecto de tipo de referencia \(`type`% o `type`&\) al tipo envolvente.  
  
-   Un direccionamiento indirecto de tipo de referencia \(`type`el ^% o ^&de `type`\) al identificador.  
  
 Puede definir los operadores siguientes:  
  
|operador ??|¿Unario\/formatos binarios?|  
|-----------------|---------------------------------|  
|\!|Unario|  
|\!\=|Binary|  
|%|Binary|  
|&|Unario y binario|  
|&&|Binary|  
|\*|Unario y binario|  
|\+|Unario y binario|  
|\+\+|Unario|  
|,|Binary|  
|\-|Unario y binario|  
|\-\-|Unario|  
|\-\>|Unario|  
|\/|Binary|  
|\<|Binary|  
|\<\<|Binary|  
|\<\=|Binary|  
|\=|Binary|  
|\=\=|Binary|  
|\>|Binary|  
|\>\=|Binary|  
|\>\>|Binary|  
|^|Binary|  
|false|Unario|  
|true|Unario|  
|&#124;|Binary|  
|&#124;&#124;|Binary|  
|~|Unario|  
  
## Ejemplo  
  
```  
// mcppv2_user-defined_operators.cpp  
// compile with: /clr  
using namespace System;  
public ref struct X {  
   X(int i) : m_i(i) {}  
   X() {}  
  
   int m_i;  
  
   // static, binary, user-defined operator  
   static X ^ operator + (X^ me, int i) {  
      return (gcnew X(me -> m_i + i));  
   }  
  
   // instance, binary, user-defined operator  
   X^ operator -( int i ) {  
      return gcnew X(this->m_i - i);  
   }  
  
   // instance, unary, user-defined pre-increment operator  
   X^ operator ++() {  
      return gcnew X(this->m_i++);  
   }  
  
   // instance, unary, user-defined post-increment operator  
   X^ operator ++(int i) {  
      return gcnew X(this->m_i++);  
   }  
  
   // static, unary user-defined pre- and post-increment operator  
   static X^ operator-- (X^ me) {  
      return (gcnew X(me -> m_i - 1));  
   }  
};  
  
int main() {  
   X ^hX = gcnew X(-5);  
   System::Console::WriteLine(hX -> m_i);  
  
   hX = hX + 1;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX = hX - (-1);  
   System::Console::WriteLine(hX -> m_i);  
  
   ++hX;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX++;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX--;  
   System::Console::WriteLine(hX -> m_i);  
  
   --hX;  
   System::Console::WriteLine(hX -> m_i);  
}  
```  
  
  **\-5**  
**\-4**  
**\-3**  
**\-2**  
**\-1**  
**\-2**  
**\-3**   
## Ejemplo  
 El ejemplo siguiente se muestra la síntesis del operador, que solo está disponible cuando se usa **\/clr** para compilar.  La síntesis del operador crea el formulario de la asignación de un operador binario, si no se define, donde el lado izquierdo del operador de asignación tiene un tipo CLR.  
  
```  
// mcppv2_user-defined_operators_2.cpp  
// compile with: /clr  
ref struct A {  
   A(int n) : m_n(n) {};  
   static A^ operator + (A^ r1, A^ r2) {  
      return gcnew A( r1->m_n + r2->m_n);  
   };  
   int m_n;  
};  
  
int main() {  
   A^ a1 = gcnew A(10);  
   A^ a2 = gcnew A(20);  
  
   a1 += a2;   // a1 = a1 + a2   += not defined in source  
   System::Console::WriteLine(a1->m_n);  
}  
```  
  
  **30**   
## Vea también  
 [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)