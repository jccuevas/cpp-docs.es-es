---
title: ___lc_codepage_func
ms.date: 4/2/2020
api_name:
- ___lc_codepage_func
- _o____lc_codepage_func
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: ea740bc335981ad7e1017ab4026fdc50b8fe8893
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914134"
---
# <a name="___lc_codepage_func"></a>___lc_codepage_func

Función de CRT interna. Recupera la página de código actual del subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Valor devuelto

Página de código actual del subproceso.

## <a name="remarks"></a>Observaciones

`___lc_codepage_func` es una función de CRT interna a la que recurren otras funciones de CRT para obtener la página de código actual del almacén local de subprocesos de datos de CRT. Esta información también se puede obtener mediante la función [_get_current_locale](../c-runtime-library/reference/get-current-locale.md).

Una *página de código* es una asignación de códigos de byte único o de doble byte a caracteres individuales. Cada página de código incluye caracteres especiales distintos, que suelen estar personalizados para un idioma o grupo de idiomas. Para obtener más información sobre las páginas de códigos, vea [Páginas de códigos](../c-runtime-library/code-pages.md).

Las funciones de CRT internas son específicas de la implementación y están sujetas a cambio en cada versión. Se desaconseja usarlas en el código.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`___lc_codepage_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Consulta también

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
