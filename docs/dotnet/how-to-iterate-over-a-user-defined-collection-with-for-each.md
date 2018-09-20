---
title: 'Cómo: iterar por una colección definida por el usuario con for each | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- collections, iterating over
ms.assetid: 0efd9e3c-d7bb-4f6c-9938-e0e65d191433
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d3556faac731b11e4933126e8890304d3878d7d6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422758"
---
# <a name="how-to-iterate-over-a-user-defined-collection-with-for-each"></a>Cómo: Iterar por una colección definida por el usuario con for each

Para que una clase sea una colección administrada, se necesita una función de GetEnumerator no privado que devuelve un identificador a una clase de enumerador o una interfaz.  Una clase de enumerador debe contener la declaración de función de MoveNext no estáticos y la propiedad actual.

## <a name="example"></a>Ejemplo

Colección con tipos de referencia definidos por el usuario sencilla.

```
// for_each_user_defined_collections.cpp
// compile with: /clr
using namespace System;
public interface struct IMyEnumerator {
   bool MoveNext();
   property Object^ Current {
      Object^ get();
   }
   void Reset();
};

public ref struct MyArray {

   MyArray( array<int>^ d ) {
      data = d;
   }

   ref struct enumerator : IMyEnumerator {
      enumerator( MyArray^ myArr ) {
         colInst = myArr;
         currentIndex = -1;
      }

      virtual bool MoveNext() {
         if( currentIndex < colInst->data->Length - 1 ) {
            currentIndex++;
            return true;
         }
         return false;
      }

      property Object^ Current {
         virtual Object^ get() {
            return colInst->data[currentIndex];
         }
      };

      virtual void Reset() {}
      ~enumerator() {}

      MyArray^ colInst;
      int currentIndex;
   };

   array<int>^ data;

   IMyEnumerator^ GetEnumerator() {
      return gcnew enumerator(this);
   }
};

int main() {
   int retval = 0;

   MyArray^ col = gcnew MyArray( gcnew array<int>{10, 20, 30 } );

   for each ( Object^ c in col )
      retval += (int)c;

   retval -= 10 + 20 + 30;

   for each ( int c in gcnew MyArray( gcnew array<int>{10, 20, 30 } ) )
      retval += c;

   retval -= 10 + 20 + 30;

   Console::WriteLine("Return Code: {0}", retval );
   return retval;
}
```

```Output
Return Code: 0
```

## <a name="see-also"></a>Vea también

[for each, in](../dotnet/for-each-in.md)