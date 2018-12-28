---
title: Funciones intrínsecas _InterlockedAdd
ms.date: 12/17/2018
f1_keywords:
- _InterlockedAdd64_acq_cpp
- _InterlockedAdd64_acq
- _InterlockedAdd_acq
- _InterlockedAdd_nf
- _InterlockedAdd64_rel
- _InterlockedAdd64
- _InterlockedAdd_cpp
- _InterlockedAdd_rel_cpp
- _InterlockedAdd_rel
- _InterlockedAdd64_rel_cpp
- _InterlockedAdd64_cpp
- _InterlockedAdd_acq_cpp
- _InterlockedAdd64_nf
- _InterlockedAdd
helpviewer_keywords:
- _InterlockedAdd_nf intrinsic
- _InterlockedAdd_rel intrinsic
- _InterlockedAdd intrinsic
- _InterlockedAdd64 intrinsic
- _InterlockedAdd64_acq intrinsic
- _InterlockedAdd64_nf intrinsic
- _InterlockedAdd_acq intrinsic
- _InterlockedAdd64_rel intrinsic
ms.assetid: 3d319603-ea9c-4fdd-ae61-e52430ccc3b1
ms.openlocfilehash: 473d113ff9af3b009075dfef657082034b1bbcb6
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626911"
---
# <a name="interlockedadd-intrinsic-functions"></a>Funciones intrínsecas _InterlockedAdd

**Específicos de Microsoft**

Estas funciones realizan una suma atómica, que se asegura de que la operación completa correctamente cuando más de un subproceso tiene acceso a una variable compartida.

## <a name="syntax"></a>Sintaxis

```
long _InterlockedAdd(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_acq(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_nf(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_rel(
   long volatile * Addend,
   long Value
);
__int64 _InterlockedAdd64(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_acq(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_nf (
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_rel(
   __int64 volatile * Addend,
   __int64 Value
);
```

#### <a name="parameters"></a>Parámetros

*Sumando*<br/>
[in, out] Puntero al entero al que se agregará; reemplaza el resultado de la suma.

*Valor*<br/>
[in] Valor que se agrega.

## <a name="return-value"></a>Valor devuelto

Ambas funciones devuelven el resultado de la suma.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_InterlockedAdd`|ARM|
|`_InterlockedAdd_acq`|ARM|
|`_InterlockedAdd_nf`|ARM|
|`_InterlockedAdd_rel`|ARM|
|`_InterlockedAdd64`|ARM|
|`_InterlockedAdd64_acq`|ARM|
|`_InterlockedAdd64_nf`|ARM|
|`_InterlockedAdd64_rel`|ARM|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

Las versiones de estas funciones con los sufijos `_acq` o `_rel` realizan una suma entrelazada tras la adquisición o la liberación de semántica. *Semántica de adquisición* significa que el resultado de la operación se hace visible para todos los subprocesos y procesadores antes de cualquier memoria posterior las lecturas y escrituras. La adquisición es útil al entrar en una sección crítica. *Semántica de liberación* significa que toda la memoria, lecturas y escrituras se ven obligado a ser visibles para todos los subprocesos y procesadores antes de que el resultado de la operación se hace visibles propio. La liberación es útil al salir de una sección crítica. Los intrínsecos con un `_nf` sufijo ("sin límite") no actúan como una barrera de memoria.

Estas rutinas solo están disponibles como intrínsecos.

## <a name="example"></a>Ejemplo

```cpp
// interlockedadd.cpp
// Compile with: /Oi /EHsc
// processor: ARM
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_InterlockedAdd)

int main()
{
        long data1 = 0xFF00FF00;
        long data2 = 0x00FF0000;
        long retval;
        retval = _InterlockedAdd(&data1, data2);
        printf("0x%x 0x%x 0x%x", data1, data2, retval);
}
```

## <a name="output"></a>Salida

```Output
0xffffff00 0xff0000 0xffffff00
```

## <a name="example"></a>Ejemplo

```cpp
// interlockedadd64.cpp
// compile with: /Oi /EHsc
// processor: ARM
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_InterlockedAdd64)

int main()
{
        __int64 data1 = 0x0000FF0000000000;
        __int64 data2 = 0x00FF0000FFFFFFFF;
        __int64 retval;
        cout << hex << data1 << " + " << data2 << " = " ;
        retval = _InterlockedAdd64(&data1, data2);
        cout << data1 << endl;
        cout << "Return value: " << retval << endl;
}
```

## <a name="output"></a>Salida

```Output
ff0000000000 + ff0000ffffffff = ffff00ffffffff
Return value: ffff00ffffffff
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Conflictos con el compilador de x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)