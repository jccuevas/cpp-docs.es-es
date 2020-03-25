---
title: _fpclass, _fpclassf
ms.date: 04/05/2018
api_name:
- _fpclass
- _fpclassf
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
ms.openlocfilehash: 982bd5fb33ef2e14785c775a9b79b0adc8f3a459
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170220"
---
# <a name="_fpclass-_fpclassf"></a>_fpclass, _fpclassf

Devuelve un valor que indica la clasificación de punto flotante del argumento.

## <a name="syntax"></a>Sintaxis

```C
int _fpclass(
   double x
);

int _fpclassf(
   float x
); /* x64 only */
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante que se va a probar.

## <a name="return-value"></a>Valor devuelto

Las funciones **_fpclass** y **_fpclassf** devuelven un valor entero que indica la clasificación de punto flotante del argumento *x*. Es posible que la clasificación tenga uno de los valores siguientes, que se definen en \<float.h>.

|Value|Descripción|
|-----------|-----------------|
|**_FPCLASS_SNAN**|NaN de señalización|
|**_FPCLASS_QNAN**|NaN reservado|
|**_FPCLASS_NINF**|Infinito negativo (-INF)|
|**_FPCLASS_NN**|Negativo normalizado distinto de cero|
|**_FPCLASS_ND**|Negativo no normalizado|
|**_FPCLASS_NZ**|Cero negativo (-0)|
|**_FPCLASS_PZ**|Cero positivo (+0)|
|**_FPCLASS_PD**|Positivo no normalizado|
|**_FPCLASS_PN**|Positivo normalizado distinto de cero|
|**_FPCLASS_PINF**|Infinito positivo (+INF)|

## <a name="remarks"></a>Observaciones

Las funciones **_fpclass** y **_fpclassf** son específicas de Microsoft. Son similares a [fpclassify](fpclassify.md), pero devuelven información más detallada sobre el argumento. La función **_fpclassf** solo está disponible cuando se compila para la plataforma x64.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fpclass**, **_fpclassf**|\<float.h>|

Para obtener más información sobre compatibilidad y conformidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>
