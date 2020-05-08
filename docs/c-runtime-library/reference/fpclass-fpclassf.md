---
title: _fpclass, _fpclassf
ms.date: 4/2/2020
api_name:
- _fpclass
- _fpclassf
- _o__fpclass
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a6591d9348739d27831785a05f4a602aacdd4d0c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914845"
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

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fpclass**, **_fpclassf**|\<float.h>|

Para obtener más información sobre compatibilidad y conformidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>
