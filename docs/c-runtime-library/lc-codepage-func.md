---
title: ___lc_codepage_func
ms.date: 11/04/2016
api_name:
- ___lc_codepage_func
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
helpviewer_keywords:
- ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
ms.openlocfilehash: dbadf8239652f5c96e7177dedd91d340e545b9fe
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944921"
---
# <a name="___lc_codepage_func"></a>___lc_codepage_func

Función de CRT interna. Recupera la página de código actual del subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Valor devuelto

Página de código actual del subproceso.

## <a name="remarks"></a>Comentarios

`___lc_codepage_func` es una función de CRT interna a la que recurren otras funciones de CRT para obtener la página de código actual del almacén local de subprocesos de datos de CRT. Esta información también se puede obtener mediante la función [_get_current_locale](../c-runtime-library/reference/get-current-locale.md).

Una *página de código* es una asignación de códigos de byte único o de doble byte a caracteres individuales. Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas. Para obtener más información sobre las páginas de códigos, vea [Code Pages](../c-runtime-library/code-pages.md).

Las funciones de CRT internas son específicas de la implementación y están sujetas a cambio en cada versión. Se desaconseja usarlas en el código.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`___lc_codepage_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Vea también

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
