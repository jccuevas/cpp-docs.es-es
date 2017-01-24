---
title: "C&#243;mo: Iterar por una colecci&#243;n gen&#233;rica con for each | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "colección genérica, recorriendo en iteración"
ms.assetid: 00288d53-3d41-44d0-be5b-b3033456ceaa
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Iterar por una colecci&#243;n gen&#233;rica con for each
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La característica de [Genéricos](../windows/generics-cpp-component-extensions.md) de Visual C\+\+ permite crear colecciones genéricas.  
  
## Ejemplo  
 Este ejemplo muestra cómo utilizar `for each` con una colección genérica simple del tipo de valor.  
  
```  
// for_each_generics.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Collections::Generic;  
  
generic <class T>  
public value struct MyArray : public IEnumerable<T> {     
  
   MyArray( array<T>^ d ) {  
      data = d;  
   }  
  
   ref struct enumerator : IEnumerator<T> {  
      enumerator( MyArray^ myArr ) {  
         colInst = myArr;  
         currentIndex = -1;  
      }  
  
      virtual bool MoveNext() = IEnumerator<T>::MoveNext {  
         if ( currentIndex < colInst->data->Length - 1 ) {  
            currentIndex++;  
            return true;  
         }  
  
         return false;  
      }  
  
      virtual property T Current {  
         T get() {  
            return colInst->data[currentIndex];  
         }  
      };  
  
      property Object^ CurrentNonGeneric {  
         virtual Object^ get() = System::Collections::IEnumerator::Current::get {  
            return colInst->data[currentIndex];  
         }  
      };  
  
      virtual void Reset() {}  
      ~enumerator() {}  
  
      MyArray^ colInst;  
      int currentIndex;  
   };  
  
   array<T>^ data;  
  
   virtual IEnumerator<T>^ GetEnumerator() {  
      return gcnew enumerator(*this);  
   }  
   virtual System::Collections::IEnumerator^ GetEnumeratorNonGeneric() = System::Collections::IEnumerable::GetEnumerator {  
      return gcnew enumerator(*this);  
   }  
};  
  
int main() {  
   MyArray<int> col = MyArray<int>( gcnew array<int>{10, 20, 30 } );  
  
   for each ( Object^ c in col )  
      Console::WriteLine((int)c);  
}  
```  
  
  **10**  
**20**  
**30**   
## Vea también  
 [for each, in](../dotnet/for-each-in.md)