---
title: __lidt
ms.date: 09/02/2019
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 24778b761ada56830b155a2fc65e90f54ba729ed
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217508"
---
# <a name="__lidt"></a>__lidt

**Específicos de Microsoft**

Carga el registro de la tabla de descriptores de interrupción (IDTR) con el valor en la ubicación de memoria especificada.

## <a name="syntax"></a>Sintaxis

```C
void __lidt(void * Source);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*Origen*|de Puntero al valor que se va a copiar en IDTR.|

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__lidt`|x86, x64|

**Archivo de encabezado** \<INTRIN. h >

## <a name="remarks"></a>Comentarios

La `__lidt` función es equivalente a la `LIDT` instrucción máquina y solo está disponible en modo kernel. Para obtener más información, busque el documento "manual del desarrollador de software de arquitectura Intel, volumen 2: Referencia del conjunto de instrucciones, en el sitio de [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[__sidt](../intrinsics/sidt.md)
