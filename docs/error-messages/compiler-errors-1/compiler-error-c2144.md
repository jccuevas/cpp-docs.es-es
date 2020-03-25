---
title: Error del compilador C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: b917c0a2c15aeb70222c948bce9a6fb275c91068
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207251"
---
# <a name="compiler-error-c2144"></a>Error del compilador C2144

> error de sintaxis: '*Type*' debe ir precedido de '*token*'

El compilador esperaba un *token* y se encontró el *tipo* en su lugar.

Este error puede deberse a que falta una llave de cierre, un paréntesis derecho o un punto y coma.

C2144 también se puede producir al intentar crear una macro a partir de una palabra clave de CLR que contiene un carácter de espacio en blanco.

También puede ver C2144 si está intentando realizar el reenvío de tipos. Consulte [reenvío de tiposC++(/CLI)](../../extensions/type-forwarding-cpp-cli.md) para obtener más información.

## <a name="examples"></a>Ejemplos

En el ejemplo siguiente se genera C2144 y se muestra una manera de corregirlo:

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

En el ejemplo siguiente se genera C2144 y se muestra una manera de corregirlo:

```cpp
// C2144_2.cpp
// compile with: /clr /c
ref struct X {

   property double MultiDimProp[,,] {   // C2144
   // try the following line instead
   // property double MultiDimProp[int , int, int] {
      double get(int, int, int) { return 1; }
      void set(int i, int j, int k, double l) {}
   }

   property double MultiDimProp2[] {   // C2144
   // try the following line instead
   // property double MultiDimProp2[int] {
      double get(int) { return 1; }
      void set(int i, double l) {}
   }
};
```
