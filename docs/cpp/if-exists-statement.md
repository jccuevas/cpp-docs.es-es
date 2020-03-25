---
title: __if_exists (Instrucción)
ms.date: 11/04/2016
f1_keywords:
- __if_exists_cpp
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
ms.openlocfilehash: ea136ac0312b78519fe2d8ea88ace4d8b0d69946
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178423"
---
# <a name="__if_exists-statement"></a>__if_exists (Instrucción)

La instrucción **__if_exists** comprueba si existe el identificador especificado. Si el identificador existe, se ejecuta el bloque de instrucción especificado.

## <a name="syntax"></a>Sintaxis

```
__if_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*identifier*|El identificador cuya existencia se desea probar.|
|*afirma*|Una o varias instrucciones que se ejecutarán si el *identificador* existe.|

## <a name="remarks"></a>Observaciones

> [!CAUTION]
>  Para obtener los resultados más confiables, utilice la instrucción **__if_exists** en las siguientes restricciones.

- Aplique la instrucción **__if_exists** solo a tipos simples, no a plantillas.

- Aplique la instrucción **__if_exists** a los identificadores tanto dentro como fuera de una clase. No aplique la instrucción **__if_exists** a las variables locales.

- Use la instrucción **__if_exists** solo en el cuerpo de una función. Fuera del cuerpo de una función, la instrucción **__if_exists** solo puede probar tipos totalmente definidos.

- Cuando se prueban funciones sobrecargadas, no se puede probar una forma específica de la sobrecarga.

El complemento a la instrucción **__if_exists** es la instrucción [__if_not_exists](../cpp/if-not-exists-statement.md) .

## <a name="example"></a>Ejemplo

Observe que este ejemplo utiliza plantillas, lo que no se recomienda.

```cpp
// the__if_exists_statement.cpp
// compile with: /EHsc
#include <iostream>

template<typename T>
class X : public T {
public:
   void Dump() {
      std::cout << "In X<T>::Dump()" << std::endl;

      __if_exists(T::Dump) {
         T::Dump();
      }

      __if_not_exists(T::Dump) {
         std::cout << "T::Dump does not exist" << std::endl;
      }
   }
};

class A {
public:
   void Dump() {
      std::cout << "In A::Dump()" << std::endl;
   }
};

class B {};

bool g_bFlag = true;

class C {
public:
   void f(int);
   void f(double);
};

int main() {
   X<A> x1;
   X<B> x2;

   x1.Dump();
   x2.Dump();

   __if_exists(::g_bFlag) {
      std::cout << "g_bFlag = " << g_bFlag << std::endl;
   }

   __if_exists(C::f) {
      std::cout << "C::f exists" << std::endl;
   }

   return 0;
}
```

## <a name="output"></a>Output

```Output
In X<T>::Dump()
In A::Dump()
In X<T>::Dump()
T::Dump does not exist
g_bFlag = 1
C::f exists
```

## <a name="see-also"></a>Consulte también

[Instrucciones de selección](../cpp/selection-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[__if_not_exists (Instrucción)](../cpp/if-not-exists-statement.md)
