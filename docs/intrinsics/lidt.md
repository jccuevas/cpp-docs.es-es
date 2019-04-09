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
ms.openlocfilehash: 757309603af48820a17668cfe272bbeaad9239b3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038478"
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

El `__lidt` función es equivalente a la `LIDT` instrucción máquina y solo está disponible en modo kernel. Para obtener más información, busque el documento, "Manual del desarrollador de Software de arquitectura Intel, volumen 2: Establecer referencia de instrucciones,"en el [Intel Corporation](https://software.intel.com/articles/intel-sdm) sitio.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__sidt](../intrinsics/sidt.md)