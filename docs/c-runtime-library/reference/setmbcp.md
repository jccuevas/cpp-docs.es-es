---
title: _setmbcp
ms.date: 4/2/2020
api_name:
- _setmbcp
- _o__setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: 61086471c6194aaa8434d291647978bf891a8aea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337601"
---
# <a name="_setmbcp"></a>_setmbcp

Establece una nueva página de códigos multibyte.

## <a name="syntax"></a>Sintaxis

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>Parámetros

*Codepage*<br/>
Nueva configuración de la página de códigos para las rutinas multibyte independientes de la configuración regional.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si la página de códigos se establece correctamente. Si se proporciona un valor de página de códigos no válido para la página de *códigos*, devuelve -1 y la configuración de la página de códigos no cambia. Establece **errno en** **EINVAL** si se produce un error de asignación de memoria.

## <a name="remarks"></a>Observaciones

La función **_setmbcp** especifica una nueva página de códigos multibyte. De forma predeterminada, el sistema en tiempo de ejecución establece automáticamente la página de códigos multibyte en la página de códigos ANSI predeterminada del sistema. La configuración de la página de códigos multibyte afecta a todas las rutinas multibyte que no dependen de la configuración regional. Sin embargo, es posible indicar a **_setmbcp** que utilice la página de códigos definida para la configuración regional actual (consulte la siguiente lista de constantes de manifiesto y resultados de comportamiento asociados). Para obtener una lista de las rutinas multibyte que dependen de la página de códigos de configuración regional, y no de la página de códigos multibyte, vea [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

La página de códigos multibyte también afecta al procesamiento de caracteres multibyte por las siguientes rutinas de la biblioteca en tiempo de ejecución:

||||
|-|-|-|
|[_exec (funciones)](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Además, todas las rutinas de biblioteca en tiempo de ejecución que reciben argumentos de programa *argv* o *envp* de caracteres multibyte como parámetros (como las familias **_exec** y **_spawn)** procesan estas cadenas según la página de códigos multibyte. Por lo tanto, estas rutinas también se ven afectadas por una llamada a **_setmbcp** que cambia la página de códigos multibyte.

El argumento de página de *códigos* se puede establecer en cualquiera de los siguientes valores:

- **_MB_CP_ANSI** Utilice la página de códigos ANSI obtenida del sistema operativo al iniciar el programa.

- **_MB_CP_LOCALE** Utilice la página de códigos de la configuración regional actual obtenida de una llamada anterior a [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** Utilice la página de códigos OEM obtenida del sistema operativo al iniciar el programa.

- **_MB_CP_SBCS** Utilice la página de códigos de un solo byte. Cuando la página de códigos se establece en **_MB_CP_SBCS**, una rutina como [_ismbblead](ismbblead-ismbblead-l.md) siempre devuelve false.

- **_MB_CP_UTF8** Utilice UTF-8.  Cuando la página de códigos se establece en **_MB_CP_UTF8**, una rutina como [_ismbblead](ismbblead-ismbblead-l.md) siempre devuelve false.

- Cualquier otro valor de página de códigos válido, independientemente de si el valor es un ANSI, OEM u otra página de códigos compatible con el sistema operativo (excepto UTF-7, que no se admite).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
