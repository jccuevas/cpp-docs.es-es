---
title: Atributo de tipos de parámetros (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, parameter types
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 84c97dc0eb449ed0a2e835c46e77981dda0b67e2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611911"
---
# <a name="attribute-parameter-types--c-component-extensions"></a>Tipos de parámetros de atributo (Extensiones de componentes de C++)

El compilador deben conocer los valores pasados a los atributos en tiempo de compilación.  Parámetros de atributo pueden ser de los siguientes tipos:

- **bool**

- **char**, **unsigned char**

- **short**, **unsigned short**

- **int**, **int sin signo**

- **Long**, **unsigned long**

- **__int64**, **__int64 sin signo**

- **float**, **dobles**

- **wchar_t**

- `char*` o `wchar_t*` o `System::String*`

- `System::Type ^`

- `System::Object ^`

- **enum**

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```cpp
// attribute_parameter_types.cpp
// compile with: /clr /c
using namespace System;
ref struct AStruct {};

[AttributeUsage(AttributeTargets::ReturnValue)]
ref struct Attr : public Attribute {
   Attr(AStruct ^ i){}
   Attr(bool i){}
   Attr(){}
};

ref struct MyStruct {
   static AStruct ^ x = gcnew AStruct;
   [returnvalue:Attr(x)] int Test() { return 0; }   // C3104
   [returnvalue:Attr] int Test2() { return 0; }   // OK
   [returnvalue:Attr(true)] int Test3() { return 0; }   // OK
};
```

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

Al especificar los atributos, todos los argumentos (posicionales) sin nombre deben preceder a cualquier argumento con nombre.

### <a name="code"></a>Código

```cpp
// extending_metadata_c.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
ref class MyAttr : public Attribute {
public:
   MyAttr() {}
   MyAttr(int i) {}
   property int Priority;
   property int Version;
};

[MyAttr]
ref class ClassA {};   // No arguments

[MyAttr(Priority = 1)]
ref class ClassB {};   // Named argument

[MyAttr(123)]
ref class ClassC {};   // Positional argument

[MyAttr(123, Version = 1)]
ref class ClassD {};   // Positional and named
```

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

Parámetros de atributo pueden ser matrices unidimensionales de los tipos anteriores.

### <a name="code"></a>Código

```cpp
// extending_metadata_d.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="see-also"></a>Vea también

[Atributos definidos por el usuario](../windows/user-defined-attributes-cpp-component-extensions.md)