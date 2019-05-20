---
title: Genéricos y plantillas (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: 74cfd791e8400b788d38f272eed3d421ca4230e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516360"
---
# <a name="generics-and-templates-ccli"></a>Genéricos y plantillas (C++/CLI)

Los genéricos y las plantillas son dos características de lenguaje que ofrecen compatibilidad con tipos parametrizados. Sin embargo, son diferentes y tienen usos diferentes. En este tema se ofrece información general de las muchas diferencias.

Para más información, consulte [Windows Runtime y plantillas administradas](windows-runtime-and-managed-templates-cpp-component-extensions.md).

## <a name="comparing-templates-and-generics"></a>Comparación de plantillas y genéricos

Principales diferencias entre genéricos y plantillas de C++:

- Los genéricos son genéricos hasta que se sustituyen sus tipos en tiempo de ejecución. Las plantillas están especializadas en tiempo de compilación, por lo que no son todavía tipos parametrizados en tiempo de ejecución

- Common Language Runtime admite en concreto genéricos de MSIL. Como el entorno de ejecución conoce los genéricos, se pueden sustituir tipos específicos por tipos genéricos al hacer referencia a un ensamblado que contiene un tipo genérico. Las plantillas, en cambio, se resuelven en tipos normales en tiempo de compilación y los tipos resultantes no se pueden especializar en otros ensamblados.

- Los genéricos especializados en dos ensamblados diferentes con los mismos argumentos de tipo son del mismo tipo. Las plantillas especializadas en dos ensamblados diferentes con los mismos argumentos de tipo se consideran de diferentes tipos en tiempo de ejecución.

- Los genéricos se generan como un único fragmento de código ejecutable que se usa en todos los argumentos de tipo de referencia (esto no se aplica a los tipos de valor, que tienen una implementación única por cada tipo de valor). El compilador JIT conoce los genéricos y es capaz de optimizar el código de los tipos de valor o referencia que se usan como argumentos de tipo. Las plantillas generan código en tiempo de ejecución independiente para cada especialización.

- Los genéricos no permiten parámetros de plantilla sin tipo, como `template <int i> C {}`. Las plantillas sí los permiten.

- Los genéricos no admiten la especialización explícita (es decir, la implementación personalizada de una plantilla para un tipo específico). Las plantillas sí lo hacen.

- Los genéricos no admiten la especialización parcial (implementación personalizada de un subconjunto de los argumentos de tipo). Las plantillas sí lo hacen.

- Los genéricos no permiten que se use el parámetro de tipo como clase base del tipo genérico. Las plantillas sí lo hacen.

- Las plantillas admiten parámetros plantilla a plantilla (por ejemplo, `template<template<class T> class X> class MyClass`), pero los genéricos no.

## <a name="combining-templates-and-generics"></a>Combinación de plantillas y genéricos

La diferencia básica de los genéricos tiene repercusiones sobre la creación de aplicaciones que combinan plantillas y genéricos. Por ejemplo, suponga que tiene una clase de plantilla para la que quiere crear un contenedor genérico a fin de exponer dicha plantilla como genérico a otros lenguajes. No puede hacer que el genérico tome un parámetro de tipo que luego pase a la plantilla, puesto que la plantilla debe tener ese parámetro de tipo en tiempo de compilación, pero el genérico no resolverá el parámetro de tipo si no es en tiempo de ejecución. Anidar una plantilla dentro de un genérico no funcionará bien porque no hay ninguna manera de expandir las plantillas en tiempo de compilación para tipos genéricos arbitrarios de los que se podrían crear instancias en tiempo de ejecución.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo siguiente se muestra un ejemplo sencillo de uso de plantillas y genéricos juntos. En este ejemplo, la clase de plantilla pasa su parámetro a través del tipo genérico. Lo contrario no es posible.

Esta expresión podría usarse cuando quiera compilar sobre una API genérica existente con el código de plantilla que es local para un ensamblado de C++/CLI, o cuando necesite agregar una capa adicional de parametrización a un tipo genérico, con el objetivo de aprovechar las ventajas de ciertas características de las plantillas que no admiten los genéricos.

### <a name="code"></a>Código

```cpp
// templates_and_generics.cpp
// compile with: /clr
using namespace System;

generic <class ItemType>
ref class MyGeneric {
   ItemType m_item;

public:
   MyGeneric(ItemType item) : m_item(item) {}
   void F() {
      Console::WriteLine("F");
   }
};

template <class T>
public ref class MyRef {
MyGeneric<T>^ ig;

public:
   MyRef(T t) {
      ig = gcnew MyGeneric<T>(t);
      ig->F();
    }
};

int main() {
   // instantiate the template
   MyRef<int>^ mref = gcnew MyRef<int>(11);
}
```

```Output
F
```

## <a name="see-also"></a>Vea también

[Genéricos](generics-cpp-component-extensions.md)