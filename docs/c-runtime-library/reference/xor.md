---
title: xor
ms.date: 11/04/2016
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- Xor
- std::xor
- std.xor
helpviewer_keywords:
- xor function
ms.assetid: 0fe9554b-d87b-4487-92ed-366c6dc21df2
ms.openlocfilehash: 44290cb42cd70370ae9bbdac2c8588bbade59577
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944827"
---
# <a name="xor"></a>xor

Alternativa al operador ^.

## <a name="syntax"></a>Sintaxis

```C

#define xor ^
```

## <a name="remarks"></a>Comentarios

La macro produce el operador ^.

## <a name="example"></a>Ejemplo

```cpp
// iso646_xor.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 3, b = 2, result;

   result= a ^ b;
   cout << result << endl;

   result= a xor_eq b;
   cout << result << endl;
}
```

```Output
1
1
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iso646.h>