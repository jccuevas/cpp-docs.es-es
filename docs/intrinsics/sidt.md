---
title: __sidt
ms.date: 09/02/2019
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: d6b685da0e02373307a3149c5b7b28213f37ad40
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222328"
---
# <a name="__sidt"></a>__sidt

**Específicos de Microsoft**

Almacena el valor del registro de la tabla del descriptor de interrupción (IDTR) en la ubicación de memoria especificada.

## <a name="syntax"></a>Sintaxis

```C
void __sidt(void * Destination);
```

### <a name="parameters"></a>Parámetros

*Destino*\
de Puntero a la ubicación de memoria donde se almacena el IDTR.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__sidt`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

La función `__sidt` equivale a la instrucción máquina `SIDT` . Para obtener más información, busque el documento "manual del desarrollador de software de arquitectura Intel, volumen 2: Referencia del conjunto de instrucciones, en el sitio de [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__lidt](../intrinsics/lidt.md)
