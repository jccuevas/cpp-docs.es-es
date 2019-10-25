---
title: __crtLCMapStringW
ms.date: 11/04/2016
api_name:
- __crtLCMapStringW
api_location:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __crtLCMapStringW
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
ms.openlocfilehash: 8d9458529e5772f31e3ae5463d3a6ff5a7b726e9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940444"
---
# <a name="__crtlcmapstringw"></a>__crtLCMapStringW

Asigna una cadena de caracteres a otra, para lo que realiza una transformación de dependiente de la configuración regional especificada. Esta función también puede usarse para generar un criterio de ordenación para la cadena de entrada.

## <a name="syntax"></a>Sintaxis

```cpp
int __crtLCMapStringW(
   LCID    Locale,
   DWORD   dwMapFlags,
   LPCWSTR lpSrcStr,
   int     cchSrc,
   LPWSTR  lpDestStr,
   int     cchDest)
```

#### <a name="parameters"></a>Parámetros

*Configuración regional*<br/>
Identificador de configuración regional. La configuración regional proporciona un contexto para la asignación de la cadena o la generación del criterio de ordenación. Una aplicación puede usar la macro `MAKELCID` para crear un identificador de configuración regional.

*dwMapFlags*<br/>
Tipo de transformación que se usará durante la asignación de la cadena o la generación del criterio de ordenación.

*lpSrcStr*<br/>
Puntero a una cadena de origen que la función asigna o usa para la generación del criterio de ordenación. Se supone que este parámetro es una cadena Unicode.

*cchSrc*<br/>
Tamaño, en caracteres, de la cadena a la que apunta el parámetro `lpSrcStr` . Este recuento puede incluir el terminador NULL o no.

Un valor `cchSrc` de -1 especifica que la cadena a la que apunta `lpSrcStr` termina en NULL. Si este es el caso y esta función se usa en su modo de asignación de cadena, la función calcula la longitud de la propia cadena y termina en NULL la cadena asignada que está almacenada en `*lpDestStr`.

*lpDestStr*<br/>
Puntero largo a un búfer en el que la función almacena la cadena asignada o el criterio de ordenación.

*cchDest*<br/>
Tamaño, en caracteres, del búfer al que apunta `lpDestStr`.

## <a name="return-value"></a>Valor devuelto

Si el valor de `cchDest` es distinto de cero, el número de caracteres (o bytes, si se especifica `LCMAP_SORTKEY` ) escrito en el búfer indica que la operación ha sido correcta. Este recuento incluye espacio para un terminador NULL.

Si el valor de `cchDest` es cero, el tamaño del búfer en caracteres (o bytes, si se especifica `LCMAP_SORTKEY` ) necesario para recibir la cadena traducida o el criterio de ordenación indica que la operación ha sido correcta. Este tamaño incluye espacio para un terminador NULL.

Cero indica un error. Para obtener información de errores extendida, realice una llamada a la función `GetLastError` .

## <a name="remarks"></a>Comentarios

Si `cchSrc` es mayor que cero y `lpSrcStr` es una cadena terminada en NULL, `__crtLCMapStringW` establece `cchSrc` en la longitud de la cadena. Después, `__crtLCMapStringW` llama a la versión de cadena de caracteres anchos (Unicode) de la función `LCMapString` con los parámetros especificados. Para obtener más información sobre los parámetros y el valor devuelto de esta función, vea la función [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__crtLCMapStringW|awint.h|