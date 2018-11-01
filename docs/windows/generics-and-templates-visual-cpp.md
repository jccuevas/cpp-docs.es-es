---
title: Genéricos y plantillas (C++ / c++ / CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: 81b2812faa2fcb7acfdc272474d22039afa24655
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660060"
---
# <a name="generics-and-templates-ccli"></a>Genéricos y plantillas (C++ / c++ / CLI)

Genéricos y plantillas son dos características de lenguaje que proporcionan compatibilidad para tipos parametrizados. Sin embargo, son diferentes y tienen usos diferentes. En este tema se proporciona información general de las numerosas diferencias.

Para obtener más información, consulte [en tiempo de ejecución de Windows y plantillas administradas](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md).

## <a name="comparing-templates-and-generics"></a>Comparación de las plantillas y genéricos

Diferencias entre genéricos y plantillas de C++:

- Los genéricos son genéricos, hasta que los tipos se sustituyen por ellos en tiempo de ejecución. Las plantillas están especializadas en tiempo de compilación, por lo que no son tipos parametrizados todavía en tiempo de ejecución

- En concreto, common language runtime admite genéricos de MSIL. Ya sabe que el tiempo de ejecución sobre los genéricos, tipos específicos se pueden sustituir por tipos genéricos cuando se hace referencia a un ensamblado que contiene un tipo genérico. Las plantillas, en cambio, se resuelven en los tipos normales en tiempo de compilación y no se pueden especializar de los tipos resultantes de otros ensamblados.

- Los genéricos especializados en dos ensamblados diferentes con el mismo tipo de argumentos son del mismo tipo. Plantillas especializados en dos ensamblados diferentes con el mismo tipo de argumentos se consideran el tiempo de ejecución diferentes tipos.

- Los genéricos se generan como un único fragmento de código ejecutable que se utiliza para todos los argumentos de tipo de referencia (Esto no es cierto para tipos de valor, que tienen una implementación única por cada tipo de valor). El compilador JIT sabe acerca de los genéricos y es capaz de optimizar el código para los tipos de valor o referencia que se usan como argumentos de tipo. Plantillas generan código en tiempo de ejecución independiente para cada especialización.

- Los genéricos no permiten los parámetros de plantilla sin tipo, como `template <int i> C {}`. Las plantillas permiten a ellos.

- Los genéricos no permite la especialización explícita (es decir, una implementación personalizada de una plantilla para un tipo específico). Las plantillas de hacer.

- Los genéricos no permiten la especialización parcial (una implementación personalizada un subconjunto de los argumentos de tipo). Las plantillas de hacer.

- Los genéricos no permiten el parámetro de tipo que se usará como la clase base para el tipo genérico. Las plantillas de hacer.

- Las plantillas admiten parámetros de plantilla de la plantilla (por ejemplo, `template<template<class T> class X> class MyClass`), pero no genéricos.

## <a name="combining-templates-and-generics"></a>Genéricos y plantillas de combinación

La diferencia en genéricos básica tiene implicaciones para la creación de aplicaciones que combinen las plantillas y genéricos. Por ejemplo, suponga que tiene una clase de plantilla que desea crear un contenedor genérico para exponer dicha plantilla a otros lenguajes, como un tipo genérico. No puede tener los genérico toman un parámetro de tipo que, a continuación, pasa aunque a la plantilla, puesto que la plantilla debe tener ese parámetro de tipo en tiempo de compilación, pero el tipo genérico no resolverá el parámetro de tipo hasta que el tiempo de ejecución. Anidar una plantilla dentro de un tipo genérico no funcionará bien porque no hay ninguna manera para expandir las plantillas en tiempo de compilación para los tipos genéricos arbitrarios que se pueden crear instancias en tiempo de ejecución.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

El ejemplo siguiente muestra un ejemplo sencillo del uso conjunto de plantillas y genéricos. En este ejemplo, la clase de plantilla pasa su parámetro a través del tipo genérico. Lo contrario no es posible.

Esta expresión podría usarse cuando desea compilar en una API genérica existente con el código de plantilla que sea local en C++ / c++ / ensamblado de la CLI, o cuando necesite agregar una capa adicional de parametrización a un tipo genérico aprovechar las ventajas de ciertas características de las plantillas no admite b y genéricos.

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

[Genéricos](../windows/generics-cpp-component-extensions.md)