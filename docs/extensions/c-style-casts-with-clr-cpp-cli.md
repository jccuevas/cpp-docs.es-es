---
title: Conversiones de estilo C con /clr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
ms.openlocfilehash: 2b7e492c62047e3b38224637f842d8a7fcbae84f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172599"
---
# <a name="c-style-casts-with-clr-ccli"></a>Conversiones de estilo C con /clr (C++/CLI)

El siguiente tema se aplica solo a Common Language Runtime.

Al usarse con tipos CLR, el compilador intenta asignar una conversión de estilo C a una de las conversiones indicadas a continuación, en el orden siguiente:

1. const_cast

2. safe_cast

3. safe_cast más const_cast

4. static_cast

5. static_cast más const_cast

Si ninguna de las conversiones indicadas anteriormente es válida y el tipo de la expresión y de destino son tipos de referencia CLR, la conversión de estilo C se asigna a una comprobación en tiempo de ejecución (instrucción MSIL castclass). De lo contrario, una conversión de estilo C se considera no válida y el compilador emite un error.

## <a name="remarks"></a>Observaciones

No se recomienda una conversión de estilo C. Al compilar con [/clr (Compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), use [safe_cast](safe-cast-cpp-component-extensions.md).

En el siguiente ejemplo se muestra una conversión de estilo C que se asigna a un operador **const_cast**.

```cpp
// cstyle_casts_1.cpp
// compile with: /clr
using namespace System;

ref struct R {};
int main() {
   const R^ constrefR = gcnew R();
   R^ nonconstR = (R^)(constrefR);
}
```

En el siguiente ejemplo se muestra una conversión de estilo C que se asigna a un operador **safe_cast**.

```cpp
// cstyle_casts_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Object ^ o = "hello";
   String ^ s = (String^)o;
}
```

En el siguiente ejemplo se muestra una conversión de estilo C que se asigna a un operador **safe-cast** más **const_cast**.

```cpp
// cstyle_casts_3.cpp
// compile with: /clr
using namespace System;

ref struct R {};
ref struct R2 : public R {};

int main() {
   const R^ constR2 = gcnew R2();
   try {
   R2^ b2DR = (R2^)(constR2);
   }
   catch(InvalidCastException^ e) {
      System::Console::WriteLine("Invalid Exception");
   }
}
```

En el siguiente ejemplo se muestra una conversión de estilo C que se asigna a un operador **static_cast**.

```cpp
// cstyle_casts_4.cpp
// compile with: /clr
using namespace System;

struct N1 {};
struct N2 {
   operator N1() {
      return N1();
   }
};

int main() {
   N2 n2;
   N1 n1 ;
   n1 = (N1)n2;
}
```

En el siguiente ejemplo se muestra una conversión de estilo C que se asigna a un operador **static-cast** más **const_cast**.

```cpp
// cstyle_casts_5.cpp
// compile with: /clr
using namespace System;
struct N1 {};

struct N2 {
   operator const N1*() {
      static const N1 n1;
      return &n1;
   }
};

int main() {
   N2 n2;
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast
}
```

En el siguiente ejemplo se muestra una conversión de estilo C que se asigna a una comprobación en tiempo de ejecución.

```cpp
// cstyle_casts_6.cpp
// compile with: /clr
using namespace System;

ref class R1 {};
ref class R2 {};

int main() {
   R1^ r  = gcnew R1();
   try {
      R2^ rr = ( R2^)(r);
   }
   catch(System::InvalidCastException^ e) {
      Console::WriteLine("Caught expected exception");
   }
}
```

En el siguiente ejemplo se muestra una conversión de estilo C no válida, lo que hace que el compilador emita un error.

```cpp
// cstyle_casts_7.cpp
// compile with: /clr
using namespace System;
int main() {
   String^s = S"hello";
   int i = (int)s;   // C2440
}
```

## <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

## <a name="see-also"></a>Consulte también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)
