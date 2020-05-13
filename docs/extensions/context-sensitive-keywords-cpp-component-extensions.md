---
title: Palabras clave contextuales (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- internal_CPP
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
ms.openlocfilehash: 53fcaf13eb56ae14841861bffd1a29376304b8d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182180"
---
# <a name="context-sensitive-keywords--ccli-and-ccx"></a>Palabras clave contextuales (C++/CLI y C++/CX)

Las *palabras clave contextuales* son elementos del lenguaje que solo se reconocen en contextos concretos. Fuera del contexto concreto, una palabra clave contextual puede ser un símbolo definido por el usuario.

## <a name="all-runtimes"></a>Todos los runtimes

### <a name="remarks"></a>Observaciones

A continuación se muestra una lista de palabras clave contextuales:

- [abstract](abstract-cpp-component-extensions.md)

- [delegate](delegate-cpp-component-extensions.md)

- [event](event-cpp-component-extensions.md)

- [finally](../dotnet/finally.md)

- [for each, in](../dotnet/for-each-in.md)

- [initonly](../dotnet/initonly-cpp-cli.md)

- `internal`

- [literal](literal-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [property](property-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- `where` (parte de [Genéricos](generics-cpp-component-extensions.md))

Para fines de legibilidad, es recomendable restringir el uso de palabras clave contextuales como símbolos definidos por el usuario.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="remarks"></a>Observaciones

(No hay ninguna observación específica de la plataforma para esta característica).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Observaciones

(No hay ninguna observación específica de la plataforma para esta característica).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo de código siguiente se muestra que, en el contexto adecuado, la palabra clave contextual **property** se puede utilizar para definir una propiedad y una variable.

```cpp
// context_sensitive_keywords.cpp
// compile with: /clr
public ref class C {
   int MyInt;
public:
   C() : MyInt(99) {}

   property int Property_Block {   // context-sensitive keyword
      int get() { return MyInt; }
   }
};

int main() {
   int property = 0;               // variable name
   C ^ MyC = gcnew C();
   property = MyC->Property_Block;
   System::Console::WriteLine(++property);
}
```

```Output
100
```

## <a name="see-also"></a>Consulte también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)
