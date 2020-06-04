---
title: __emul, __emulu
ms.date: 09/02/2019
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
ms.openlocfilehash: 16b2b38f6f44b99c9f5b9370ba586342a860684e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216743"
---
# <a name="__emul-__emulu"></a>__emul, __emulu

**Específicos de Microsoft**

Realiza multiplicaciones que desbordan lo que puede contener un entero de 32 bits.

## <a name="syntax"></a>Sintaxis

```C
__int64 __emul(
   int a,
   int b
);
unsigned __int64 __emulu(
   unsigned int a,
   unsigned int b
);
```

### <a name="parameters"></a>Parámetros

*un*\
de Primer operando entero de la multiplicación.

*b*\
de Segundo operando entero de la multiplicación.

## <a name="return-value"></a>Valor devuelto

Resultado de la multiplicación.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__emul`|x86, x64|
|`__emulu`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

`__emul`toma valores con signo de 2 32 bits y devuelve el resultado de la multiplicación como un valor entero de 64 bits con signo.

`__emulu`toma valores enteros sin signo de 2 32 bits y devuelve el resultado de la multiplicación como un valor entero de 64 bits sin signo.

## <a name="example"></a>Ejemplo

```cpp
// emul.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__emul)
#pragma intrinsic(__emulu)

int main()
{
   int a = -268435456;
   int b = 2;

   __int64 result = __emul(a, b);

   cout << a << " * " << b << " = " << result << endl;

   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295
   unsigned int ub = 0xF000000;  // Dec value: 251658240

   unsigned __int64 uresult = __emulu(ua, ub);

   cout << ua << " * " << ub << " = " << uresult << endl;

}
```

## <a name="output"></a>Salida

```Output
-268435456 * 2 = -536870912
4294967295 * 251658240 = 1080863910317260800
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)
