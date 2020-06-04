---
title: Error del compilador C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: 1861810f4598fa81d1b7662a57651b1648de1317
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749053"
---
# <a name="compiler-error-c3904"></a>Error del compilador C3904

' property_accessor ': debe especificar los parámetros de número

Compruebe el número de parámetros de los métodos de `get` y `set` con las dimensiones de propiedad.

- El número de parámetros para el método `get` debe ser igual al número de dimensiones de la propiedad o ser cero para las propiedades no indizadas.

- El número de parámetros del método `set` debe ser uno más que el número de dimensiones de la propiedad.

Para obtener más información, consulta [property](../../extensions/property-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3904.

```cpp
// C3904.cpp
// compile with: /clr /c
ref class X {
   property int P {
      // set
      void set();   // C3904
      // try the following line instead
      // void set(int);

      // get
      int get(int, int);   // C3904
      // try the following line instead
      // int get();
   };
};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3904.

```cpp
// C3904b.cpp
// compile with: /clr /c
ref struct X {
   property int Q[double, double, float, float, void*, int] {
      // set
      void set(double, void*);   // C3904
      // try the following line instead
      // void set(double, double, float, float, void*, int, int);

      // get
      int get();   // C3904
      // try the following line instead
      // int get(double, double, float, float, void*, int);
   }
};
```
