---
title: __sidt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __sidt
dev_langs:
- C++
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e185b04c5a23d7ee476c2cd1954c15df795cb57
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820326"
---
# <a name="sidt"></a>__sidt

**Específicos de Microsoft**

Almacena el valor del registro de tabla de interrupciones descriptor (IDTR) en la ubicación de memoria especificada.

## <a name="syntax"></a>Sintaxis

```
void __sidt(void * Destination);
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Destino*|[in] Un puntero a la ubicación de memoria donde se almacena el IDTR.|

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`__sidt`|x86, x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

El `__sidt` función es equivalente a la `SIDT` instrucción máquina. Para obtener más información, busque el documento, "Manual del desarrollador de Software de arquitectura Intel, volumen 2: referencia de conjunto de instrucciones," en el [Intel Corporation](https://software.intel.com/articles/intel-sdm) sitio.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__lidt](../intrinsics/lidt.md)