---
title: ___lc_locale_name_func
ms.date: 11/04/2016
api_name:
- ___lc_locale_name_func
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: abc1ade393538586ad07f57e6838591833c9948b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944230"
---
# <a name="___lc_locale_name_func"></a>___lc_locale_name_func

Función de CRT interna. Recupera el nombre de configuración regional local del subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
wchar_t** ___lc_locale_name_func(void);
```

## <a name="return-value"></a>Valor devuelto

Puntero a una cadena que contiene el nombre de configuración regional local del subproceso.

## <a name="remarks"></a>Comentarios

`___lc_locale_name_func` es una función de CRT interna a la que recurren otras funciones de CRT para obtener el nombre de configuración local actual del almacén local de subprocesos de datos de CRT. Esta información también se puede obtener mediante las funciones [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) o [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

Las funciones de CRT internas son específicas de la implementación y están sujetas a cambio en cada versión. Se desaconseja usarlas en el código.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Vea también

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
