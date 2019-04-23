---
title: __sidt
ms.date: 11/04/2016
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: 88dbb4713577fcf224e1c5646bf4c38b2a1dfafe
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036765"
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

La función `__sidt` equivale a la instrucción máquina `SIDT` . Para obtener más información, busque el documento, "Manual del desarrollador de Software de arquitectura Intel, volumen 2: Establecer referencia de instrucciones,"en el [Intel Corporation](https://software.intel.com/articles/intel-sdm) sitio.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[__lidt](../intrinsics/lidt.md)