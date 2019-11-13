---
title: ADVERTENCIA del compilador (nivel 1) C4930
ms.date: 11/04/2016
f1_keywords:
- C4930
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
ms.openlocfilehash: b21cc6364692eb2f3b1d56b03d175df1f2ad7ee8
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050281"
---
# <a name="compiler-warning-level-1-c4930"></a>ADVERTENCIA del compilador (nivel 1) C4930

' prototype ': no se ha llamado a la función prototipo (¿se ha diseñado una definición de variable?)

El compilador detectó un prototipo de función no utilizado. Si el prototipo se diseñó como una declaración de variable, quite los paréntesis de apertura y cierre.

En el ejemplo siguiente se genera C4930:

```cpp
// C4930.cpp
// compile with: /W1
class Lock {
public:
   int i;
};

void f() {
   Lock theLock();   // C4930
   // try the following line instead
   // Lock theLock;
}

int main() {
}
```

C4930 también se puede producir cuando el compilador no puede distinguir entre una declaración de prototipo de función y una llamada de función.

En el ejemplo siguiente se genera C4930:

```cpp
// C4930b.cpp
// compile with: /EHsc /W1

class BooleanException
{
   bool _result;

public:
   BooleanException(bool result)
      : _result(result)
   {
   }

   bool GetResult() const
   {
      return _result;
   }
};

template<class T = BooleanException>
class IfFailedThrow
{
public:
   IfFailedThrow(bool result)
   {
      if (!result)
      {
         throw T(result);
      }
   }
};

class MyClass
{
public:
   bool MyFunc()
   {
      try
      {
         IfFailedThrow<>(MyMethod()); // C4930

         // try one of the following lines instead
         // IfFailedThrow<> ift(MyMethod());
         // IfFailedThrow<>(this->MyMethod());
         // IfFailedThrow<>((*this).MyMethod());

         return true;
      }
      catch (BooleanException e)
      {
         return e.GetResult();
      }
   }

private:
   bool MyMethod()
   {
      return true;
   }
};

int main()
{
   MyClass myClass;
   myClass.MyFunc();
}
```

En el ejemplo anterior, el resultado de un método que toma cero argumentos se pasa como argumento al constructor de una variable de clase local sin nombre. Se puede eliminar la ambigüedad de la llamada mediante el nombre de la variable local o el prefijo de la llamada al método con una instancia del objeto junto con el operador de puntero a miembro adecuado.