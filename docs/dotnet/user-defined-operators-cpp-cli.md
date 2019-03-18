---
title: Operadores definidos por el usuario (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
ms.openlocfilehash: 462d0d2819d4c65b0e37d39f24566a7152a44cf3
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739985"
---
# <a name="user-defined-operators-ccli"></a>Operadores definidos por el usuario (C++/CLI)

Se permiten operadores definidos por el usuario para los tipos administrados como miembros estáticos o miembros de instancia, o en el ámbito global. Sin embargo, solo los operadores estáticos son accesibles a través de los metadatos a los clientes que están escritos en un lenguaje distinto de Visual C++.

En un tipo de referencia, uno de los parámetros de un operador estático definido por el usuario debe ser uno de los siguientes:

- Un identificador (`type` ^) a una instancia del tipo envolvente.

- Un direccionamiento indirecto de tipo de referencia (`type`^ & o tipo ^ %) en un identificador para una instancia del tipo envolvente.

En un tipo de valor, uno de los parámetros de un operador estático definido por el usuario debe ser uno de los siguientes:

- Del mismo tipo que el tipo de valor envolvente.

- Un direccionamiento indirecto de tipo de puntero (`type`^) para el tipo envolvente.

- Un direccionamiento indirecto de tipo de referencia (`type`% o `type`&) para el tipo envolvente.

- Un direccionamiento indirecto de tipo de referencia (`type`^ % o `type`^ &) para el identificador.

Puede definir los operadores siguientes:

|Operador|¿Unario/binario formularios?|
|--------------|--------------------------|
|!|Unario|
|!=|Binary|
|%|Binary|
|&|Unario y binario|
|&&|Binary|
|*|Unario y binario|
|+|Unario y binario|
|++|Unario|
|,|Binary|
|-|Unario y binario|
|--|Unario|
|->|Unario|
|/|Binary|
|<|Binary|
|<<|Binary|
|\<=|Binary|
|=|Binary|
|==|Binary|
|>|Binary|
|>=|Binary|
|>>|Binary|
|^|Binary|
|False|Unario|
|true|Unario|
|&#124;|Binary|
|&#124;&#124;|Binary|
|~|Unario|

## <a name="example"></a>Ejemplo

```cpp
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

```Output
-5
-4
-3
-2
-1
-2
-3
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra la síntesis del operador, que solo está disponible cuando se usa **/CLR** para compilar. Síntesis del operador crea el formulario de asignación de un operador binario, si uno no está definido, donde el lado izquierdo del operador de asignación tiene un tipo CLR.

```cpp
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

```Output
30
```

## <a name="see-also"></a>Vea también

[Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)
