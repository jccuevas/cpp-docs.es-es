---
title: _cgets_s, _cgetws_s
ms.date: 4/2/2020
api_name:
- _cgetws_s
- _cgets_s
- _o__cgets_s
- _o__cgetws_s
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
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
ms.openlocfilehash: b4871ff2c362e2c6cbe37be6a31bde4e6e258709
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333545"
---
# <a name="_cgets_s-_cgetws_s"></a>_cgets_s, _cgetws_s

Obtiene una cadena de caracteres de la consola. Estas versiones de [_cgets y _cgetws](../../c-runtime-library/cgets-cgetws.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _cgets_s(
   char *buffer,
   size_t numberOfElements,
   size_t *pSizeRead
);
errno_t _cgetws_s(
   wchar_t *buffer
   size_t numberOfElements,
   size_t *pSizeRead
);
template <size_t size>
errno_t _cgets_s(
   char (&buffer)[size],
   size_t *pSizeRead
); // C++ only
template <size_t size>
errno_t _cgetws_s(
   wchar_t (&buffer)[size],
   size_t *pSizeRead
); // C++ only
```

### <a name="parameters"></a>Parámetros

*Búfer*<br/>
Ubicación de almacenamiento de los datos.

*numberOfElements*<br/>
Tamaño del búfer en caracteres anchos o de un solo byte, que también es el número máximo de caracteres que se va a leer.

*pSizeRead*<br/>
Número de caracteres que realmente se va a leer.

## <a name="return-value"></a>Valor devuelto

El valor devuelto es cero si es correcto; en caso contrario, un código de error si se produce un error.

### <a name="error-conditions"></a>Condiciones de error

|*Búfer*|*numberOfElements*|*pSizeRead*|Valor devuelto|Contenido del *búfer*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**Null**|cualquiera|cualquiera|**EINVAL**|N/D|
|no **NULL**|cero|cualquiera|**EINVAL**|no modificado|
|no **NULL**|cualquiera|**Null**|**EINVAL**|cadena de longitud cero|

## <a name="remarks"></a>Observaciones

**_cgets_s** y **_cgetws_s** leer una cadena de la consola y copiar la cadena (con un terminador nulo) en el *búfer.* **_cgetws_s** es la versión de caracteres anchos de la función; que no sea el tamaño del carácter, el comportamiento de estas dos funciones es idéntico. El tamaño máximo de la cadena que se va a leer se pasa como el *numberOfElements* parámetro. Este tamaño debe incluir un carácter adicional para el carácter null de terminación. El número real de caracteres leídos se coloca en *pSizeRead*.

Si se produce un error durante la operación o en la validación de los parámetros, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y se devuelve **EINVAL.**

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina la necesidad de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores menos seguras con sus homólogos más seguros y más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_cgets_s**|\<conio.h>|
|**_cgetws_s**|\<conio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[E/S de consola y puerto](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
