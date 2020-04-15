---
title: ___lc_locale_name_func
ms.date: 4/2/2020
api_name:
- ___lc_locale_name_func
- _o____lc_locale_name_func
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: f38d4d9b11189a8313b26dd3313a5def800c2410
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351113"
---
# <a name="___lc_locale_name_func"></a>___lc_locale_name_func

Función de CRT interna. Recupera el nombre de configuración regional local del subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
wchar_t** ___lc_locale_name_func(void);
```

## <a name="return-value"></a>Valor devuelto

Puntero a una cadena que contiene el nombre de configuración regional local del subproceso.

## <a name="remarks"></a>Observaciones

`___lc_locale_name_func` es una función de CRT interna a la que recurren otras funciones de CRT para obtener el nombre de configuración local actual del almacén local de subprocesos de datos de CRT. Esta información también se puede obtener mediante las funciones [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) o [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

Las funciones de CRT internas son específicas de la implementación y están sujetas a cambio en cada versión. Se desaconseja usarlas en el código.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Consulte también

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
