---
title: __movsq
ms.date: 11/04/2016
f1_keywords:
- __movsq
helpviewer_keywords:
- __movsq intrinsic
- rep movsq instruction
- movsq instruction
ms.assetid: be116a6e-2176-4ca4-93b1-9ccf3e7e7835
ms.openlocfilehash: 4e4908cd5ffc28840b5a48b735048cccb557e97c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036752"
---
# <a name="movsq"></a>__movsq

**Específicos de Microsoft**

Genera una cadena de mover repetidas (`rep movsq`) instrucción.

## <a name="syntax"></a>Sintaxis

```
void __movsq(
   unsigned char* Dest,
   unsigned char* Source,
   size_t Count
);
```

#### <a name="parameters"></a>Parámetros

*dest*<br/>
[out] El destino de la operación.

*Origen*<br/>
[in] El origen de la operación.

*Recuento*<br/>
[in] El número de palabras cuádruples para copiar.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__movsq`|x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

El resultado es que la primera `Count` palabras cuádruples apunta `Source` se copian en el `Dest` cadena.

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```
// movsq.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsq)

int main()
{
    unsigned __int64 a1[10];
    unsigned __int64 a2[10] = {950, 850, 750, 650, 550, 450, 350, 250,
                               150, 50};
    __movsq(a1, a2, 10);

    for (int i = 0; i < 10; i++)
       printf_s("%d ", a1[i]);
    printf_s("\n");
}
```

```Output
950 850 750 650 550 450 350 250 150 50
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)