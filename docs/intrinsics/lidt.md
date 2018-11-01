---
title: __lidt
ms.date: 11/04/2016
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 8ac86674dfa0dc269328854d363db24922cf20ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623891"
---
# <a name="lidt"></a>__lidt

**Específicos de Microsoft**

Carga el registro de tabla del descriptor de interrupción (IDTR) con el valor en la ubicación de memoria especificada.

## <a name="syntax"></a>Sintaxis

```
void __lidt(void * Source);
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Origen*|[in] Puntero al valor que se copiarán en el IDTR.|

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__lidt`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

El `__lidt` función es equivalente a la `LIDT` instrucción máquina y solo está disponible en modo kernel. Para obtener más información, busque el documento, "Manual del desarrollador de Software de arquitectura Intel, volumen 2: referencia de conjunto de instrucciones," en el [Intel Corporation](https://software.intel.com/articles/intel-sdm) sitio.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__sidt](../intrinsics/sidt.md)