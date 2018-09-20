---
title: nullptr (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0596276589790ee6fae8e071e50b4d9b55dd8b85
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439619"
---
# <a name="nullptr--c-component-extensions"></a>nullptr (Extensiones de componentes de C++)

El **nullptr** palabra clave representa un *el valor de puntero null*. Use un valor de puntero nulo para indicar que un identificador de objeto, puntero interior o tipo de puntero nativo no apunta a un objeto.

Use **nullptr** con código administrado o nativo. El compilador emite instrucciones diferentes pero adecuadas para los valores de puntero nulo administrado y nativo. Para obtener información sobre el uso de la versión de C++ estándar ISO de esta palabra clave, consulte [nullptr](../cpp/nullptr.md).

El **__nullptr** palabra clave es una palabra clave específica de Microsoft que tiene el mismo significado que **nullptr**, pero se aplica a código nativo solamente. Si usas **nullptr** código C/C ++ nativo y, a continuación, compile con el [/CLR](../build/reference/clr-common-language-runtime-compilation.md) opción del compilador, el compilador no puede determinar si **nullptr** indica nativo o administrar el valor de puntero nulo. Para hacer que su intención clara al compilador, utilice **nullptr** para especificar un valor administrado o **__nullptr** para especificar un valor nativo.

El **nullptr** es equivalente a la palabra clave **nada** en Visual Basic y **null** en C#.

## <a name="usage"></a>Uso

El **nullptr** palabra clave puede utilizarse en cualquier lugar puede utilizarse un identificador, un puntero nativo o un argumento de función.

El **nullptr** palabra clave no es un tipo y no se admite para su uso con:

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (aunque `throw (Object^)nullptr;` funcionará)

El **nullptr** palabra clave puede utilizarse en la inicialización de los siguientes tipos de puntero:

- Puntero nativo

- Identificador de Windows en tiempo de ejecución

- Identificador administrado

- Puntero interior administrado

El **nullptr** palabra clave puede utilizarse para probar si un puntero o identificador de referencia es null antes de que se usa la referencia.

Las llamadas de función entre idiomas que utilizan los valores de puntero nulo para la comprobación de errores se deben interpretar correctamente.

No se puede inicializar un identificador de cero; solo **nullptr** se puede usar. Asignación de la constante 0 a un identificador de objeto produce una conversión boxing `Int32` y una conversión a `Object^`.

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra que el **nullptr** se puede usar la palabra clave siempre que sea un identificador, un puntero nativo, o se puede usar el argumento de función. Y en el ejemplo se muestra que el **nullptr** palabra clave se puede usar para comprobar una referencia antes de utilizarse.

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

En el ejemplo de código siguiente se muestra que **nullptr** y cero se puede usar indistintamente en punteros nativos.

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

En el ejemplo de código siguiente se muestra que **nullptr** se interpreta como un identificador de cualquier tipo o un puntero nativo a cualquier tipo. En el caso de sobrecarga con controladores para diferentes tipos de funciones, se generará un error de ambigüedad. El **nullptr** tendría que convertirse explícitamente a un tipo.

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

En el ejemplo de código siguiente se muestra esa conversión **nullptr** se permite y devuelve un puntero o identificador para el tipo de conversión de tipos que contiene el **nullptr** valor.

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

En el ejemplo de código siguiente se muestra que **nullptr** puede usarse como un parámetro de función.

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

En el ejemplo de código siguiente se muestra que cuando los identificadores se declaran y no se inicializaron explícitamente, son predeterminado que se inicializa en **nullptr**.

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

En el ejemplo de código siguiente se muestra que **nullptr** puede asignarse a un puntero nativo cuando se compila con `/clr`.

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>Requisitos

Opción del compilador: (no requerido; compatible con todas las opciones de generación de código, incluidas `/ZW` y `/clr`)

## <a name="see-also"></a>Vea también

[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)