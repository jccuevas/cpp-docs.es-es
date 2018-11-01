---
title: Error del compilador C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: f6472fc70ee4a86bed1422941e758127009f14cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483335"
---
# <a name="compiler-error-c2144"></a>Error del compilador C2144

> error de sintaxis: '*tipo*'debe ir precedido por'*token*'

El compilador esperado *token* y encontrar *tipo* en su lugar.

Este error puede deberse a una llave de cierre que faltan, paréntesis de cierre o punto y coma.

C2144 también puede producirse al intentar crear una macro de una palabra clave CLR que contiene un carácter de espacio en blanco.

También puede ver C2144 si intenta el reenvío de tipos. Consulte [reenvío de tipos (C++ / c++ / CLI)](../../windows/type-forwarding-cpp-cli.md) para obtener más información.

## <a name="examples"></a>Ejemplos

El ejemplo siguiente genera C2144 y muestra cómo corregirlo:

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

El ejemplo siguiente genera C2144 y muestra cómo corregirlo:

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