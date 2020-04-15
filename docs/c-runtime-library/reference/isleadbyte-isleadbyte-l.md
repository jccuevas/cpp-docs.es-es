---
title: isleadbyte, _isleadbyte_l
ms.date: 4/2/2020
api_name:
- _isleadbyte_l
- isleadbyte
- _o__isleadbyte_l
- _o_isleadbyte
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _istleadbyte
- _isleadbyte_l
- isleadbyte
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
ms.openlocfilehash: dddf1d669f77805df8e00f506b6427603ac8fd9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343835"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte, _isleadbyte_l

Determina si un carácter es el byte inicial de un carácter multibyte.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parámetros

*C*<br/>
Entero que se va a probar.

## <a name="return-value"></a>Valor devuelto

**isleadbyte** devuelve un valor distinto de cero si el argumento satisface la condición de prueba o 0 si no lo hace. En la configuración regional "C" y en las configuraciones regionales de juego de caracteres de un solo byte (SBCS), **isleadbyte** siempre devuelve 0.

## <a name="remarks"></a>Observaciones

La macro **isleadbyte** devuelve un valor distinto de cero si su argumento es el primer byte de un carácter multibyte. **isleadbyte** produce un resultado significativo para cualquier argumento entero de -1 (**EOF**) a **UCHAR_MAX** (0xFF), ambos inclusive.

El tipo de argumento esperado de **isleadbyte** es **int**; si se pasa un carácter firmado, el compilador puede convertirlo en un entero por extensión de signo, lo que produce resultados impredecibles.

La versión de esta función con el sufijo **_l** es idéntica, excepto que utiliza la configuración regional pasada en lugar de la configuración regional actual para su comportamiento dependiente de la configuración regional.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Siempre devuelve false|**_isleadbyte**|Siempre devuelve false|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[rutinas _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
