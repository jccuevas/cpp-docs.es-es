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
ms.openlocfilehash: 9d5a0b24bb08a9485b2d212058fa8f0bd82e5842
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183679"
---
# <a name="ifexists-statement"></a>__if_exists (Instrucción)

El **__if_exists** instrucción comprueba si existe el identificador especificado. Si el identificador existe, se ejecuta el bloque de instrucción especificado.

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
|*statements*|Una o varias instrucciones que se ejecutarán si *identificador* existe.|

## <a name="remarks"></a>Comentarios

> [!CAUTION]
>  Para lograr los resultados más confiables, use el **__if_exists** instrucción con las restricciones siguientes.

- Aplicar el **__if_exists** instrucción solo a tipos simples, no a plantillas.

- Aplicar el **__if_exists** instrucción a identificadores tanto dentro como fuera de una clase. No se aplican los **__if_exists** instrucción a variables locales.

- Use la **__if_exists** instrucción sólo en el cuerpo de una función. Fuera del cuerpo de una función, el **__if_exists** instrucción puede probar solo tipos totalmente definidos.

- Cuando se prueban funciones sobrecargadas, no se puede probar una forma específica de la sobrecarga.

El complemento para el **__if_exists** instrucción es la [__if_not_exists](../cpp/if-not-exists-statement.md) instrucción.

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

## <a name="output"></a>Salida

```Output
In X<T>::Dump()
In A::Dump()
In X<T>::Dump()
T::Dump does not exist
g_bFlag = 1
C::f exists
```

## <a name="see-also"></a>Vea también

[Instrucciones de selección](../cpp/selection-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[__if_not_exists (Instrucción)](../cpp/if-not-exists-statement.md)