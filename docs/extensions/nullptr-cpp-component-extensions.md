---
title: nullptr (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 05aaaa8a0d0056e0f5318f5e9329d90824760728
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515640"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C++/CLI y C++/CX)

La palabra clave **nullptr** representa un *valor de puntero nulo*. Use un valor de puntero nulo para indicar que un tipo de identificador de objeto, puntero interior o puntero nativo no apunta a un objeto.

Use **nullptr** con código administrado o nativo. El compilador emite instrucciones adecuadas pero diferentes para los valores de puntero nulo administrado y nativo. Para obtener información sobre la versión de C++ estándar de ISO de esta palabra clave, consulte [nullptr](../cpp/nullptr.md).

La palabra clave **__nullptr** es una palabra clave específica de Microsoft que tiene la misma finalidad que **nullptr**, pero solo se aplica a código nativo. Si usa **nullptr** con código de C/C++ nativo y, a continuación, compila con la opción del compilador [/clr](../build/reference/clr-common-language-runtime-compilation.md), el compilador no puede determinar si **nullptr** indica un valor de puntero nulo nativo o administrado. Para que el compilador tenga clara su intención, use **nullptr** para especificar un valor administrado o **__nullptr** para especificar un valor nativo.

La palabra clave **nullptr** equivale a **Nothing** en Visual Basic y **null** en C#.

## <a name="usage"></a>Uso

La palabra clave **nullptr** se puede usar en cualquier lugar donde pueda utilizarse un identificador, un puntero nativo o un argumento de funciones.

La palabra clave **nullptr** no es un tipo y no es compatible con:

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (aunque `throw (Object^)nullptr;` funcionará)

La palabra clave **nullptr** se puede usar en la inicialización de los siguientes tipos de puntero:

- Puntero nativo

- Identificador de Windows Runtime

- Identificador administrado

- Puntero interior administrado

La palabra clave **nullptr** se puede usar para probar si una referencia de identificador o puntero es nula antes de utilizarse.

Las llamadas de función entre los lenguajes que usan valores de puntero nulo para la comprobación de errores deben interpretarse correctamente.

No puede inicializar un identificador en cero; solo se puede usar **nullptr**. La asignación de la constante 0 a un identificador de objeto produce un valor de tipo `Int32` con conversión boxing y una conversión en `Object^`.

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra que la palabra clave **nullptr** se puede usar siempre que pueda utilizarse un identificador, un puntero nativo o un argumento de funciones. Y en el ejemplo se muestra que la palabra clave **nullptr** se puede usar para comprobar una referencia antes de utilizarse.

```cpp
// mcpp_nullptr.cpp
// compile with: /clr
value class V {};
ref class G {};
void f(System::Object ^) {}

int main() {
// Native pointer.
   int *pN = nullptr;
// Managed handle.
   G ^pG = nullptr;
   V ^pV1 = nullptr;
// Managed interior pointer.
   interior_ptr<V> pV2 = nullptr;
// Reference checking before using a pointer.
   if (pN == nullptr) {}
   if (pG == nullptr) {}
   if (pV1 == nullptr) {}
   if (pV2 == nullptr) {}
// nullptr can be used as a function argument.
   f(nullptr);   // calls f(System::Object ^)
}
```

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra que **nullptr** y cero se pueden usar indistintamente en punteros nativos.

```cpp
// mcpp_nullptr_1.cpp
// compile with: /clr
class MyClass {
public:
   int i;
};

int main() {
   MyClass * pMyClass = nullptr;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");

   pMyClass = 0;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");
}
```

```Output
pMyClass == nullptr

pMyClass == 0

pMyClass == nullptr

pMyClass == 0
```

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra que **nullptr** se interpreta como un controlador para cualquier tipo o un puntero nativo de cualquier tipo. En caso de sobrecarga de funciones con identificadores para diversos tipos, se generará un error de ambigüedad. **nullptr** tendría que convertirse explícitamente en un tipo.

```cpp
// mcpp_nullptr_2.cpp
// compile with: /clr /LD
void f(int *){}
void f(int ^){}

void f_null() {
   f(nullptr);   // C2668
   // try one of the following lines instead
   f((int *) nullptr);
   f((int ^) nullptr);
}
```

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra que la conversión **nullptr** se permite y devuelve un puntero o identificador para el tipo de conversión que contiene el valor **nullptr**.

```cpp
// mcpp_nullptr_3.cpp
// compile with: /clr /LD
using namespace System;
template <typename T>
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type

int main() {
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)

   // Delete the following line to resolve.
   f(nullptr);

   f(0);   // T = int, call f(int)
}
```

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra que **nullptr** se puede usar como parámetro de la función.

```cpp
// mcpp_nullptr_4.cpp
// compile with: /clr
using namespace System;
void f(Object ^ x) {
   Console::WriteLine("test");
}

int main() {
   f(nullptr);
}
```

```Output
test
```

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra que cuando los identificadores se declaran y no se inicializan explícitamente, se inicializan de forma predeterminada en **nullptr**.

```cpp
// mcpp_nullptr_5.cpp
// compile with: /clr
using namespace System;
ref class MyClass {
public:
   void Test() {
      MyClass ^pMyClass;   // gc type
      if (pMyClass == nullptr)
         Console::WriteLine("NULL");
   }
};

int main() {
   MyClass ^ x = gcnew MyClass();
   x -> Test();
}
```

```Output
NULL
```

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra que **nullptr** se puede asignar a un puntero nativo al compilar con `/clr`.

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>Requisitos

Opción del compilador: (no obligatoria; compatible con todas las opciones de generación de código, incluidos `/ZW` y `/clr`)

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)