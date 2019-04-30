---
title: _setmbcp
ms.date: 11/04/2016
apiname:
- _setmbcp
apilocation:
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
apitype: DLLExport
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: c1f4967baa5fda68a7df33bcd08935dca23fab16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356464"
---
# <a name="setmbcp"></a>_setmbcp

Establece una nueva página de códigos multibyte.

## <a name="syntax"></a>Sintaxis

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>Parámetros

*codepage*<br/>
Nueva configuración de la página de códigos para las rutinas multibyte independientes de la configuración regional.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si la página de códigos se establece correctamente. Si se proporciona un valor de la página de códigos no válido para *codepage*, devuelve -1 y la configuración de la página de códigos no se ha modificado. Conjuntos de **errno** a **EINVAL** si se produce un error de asignación de memoria.

## <a name="remarks"></a>Comentarios

El **_setmbcp** función especifica una nueva página de códigos multibyte. De forma predeterminada, el sistema en tiempo de ejecución establece automáticamente la página de códigos multibyte en la página de códigos ANSI predeterminada del sistema. La configuración de la página de códigos multibyte afecta a todas las rutinas multibyte que no dependen de la configuración regional. Sin embargo, es posible indicar a **_setmbcp** para usar la página de códigos definida para la configuración regional actual (consulte la siguiente lista de constantes de manifiesto y asociados de los resultados de comportamiento). Para obtener una lista de las rutinas multibyte que dependen de la página de códigos de configuración regional, y no de la página de códigos multibyte, vea [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

La página de códigos multibyte también afecta al procesamiento de caracteres multibyte por las siguientes rutinas de la biblioteca en tiempo de ejecución:

||||
|-|-|-|
|[_exec (funciones)](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Además, todas las rutinas de biblioteca en tiempo de ejecución que reciben el juego de caracteres multibyte *argv* o *envp* argumentos como parámetros de programa (como el **_exec** y **_spawn** familias) procesan estas cadenas según la página de códigos multibyte. Por lo tanto, estas rutinas también vienen determinados por una llamada a **_setmbcp** que cambia la página de códigos multibyte.

El *codepage* argumento se puede establecer en cualquiera de los siguientes valores:

- **_MB_CP_ANSI** página de códigos ANSI de uso obtenida del sistema operativo al iniciar el programa.

- **_MB_CP_LOCALE** uso página de códigos de la configuración regional actual obtenida de una llamada anterior a [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** página de códigos OEM del uso obtenida del sistema operativo al iniciar el programa.

- **_MB_CP_SBCS** use la página de código de byte único. Cuando se establece la página de códigos en **_MB_CP_SBCS**, una rutina como [_ismbblead](ismbblead-ismbblead-l.md) siempre devuelve false.

- Cualquier otro valor válido de página de códigos, independientemente de si el valor es una página de códigos de ANSI, OEM o una página de códigos compatible con otros sistemas operativos (excepto UTF-7 y UTF-8, que no son compatibles).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
