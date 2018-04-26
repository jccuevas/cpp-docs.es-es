---
title: _setmbcp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e879d4cf6ebc7cb7f61199b3bb52f1a5e3f5389
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

*página de códigos*<br/>
Nueva configuración de la página de códigos para las rutinas multibyte independientes de la configuración regional.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si la página de códigos se establece correctamente. Si se proporciona un valor de la página de códigos no válida para *codepage*, devuelve -1 y la configuración de la página de código se ha modificado. Conjuntos de **errno** a **EINVAL** si se produce un error de asignación de memoria.

## <a name="remarks"></a>Comentarios

El **_setmbcp** función especifica una nueva página de códigos multibyte. De forma predeterminada, el sistema en tiempo de ejecución establece automáticamente la página de códigos multibyte en la página de códigos ANSI predeterminada del sistema. La configuración de la página de códigos multibyte afecta a todas las rutinas multibyte que no dependen de la configuración regional. Sin embargo, es posible indicar a **_setmbcp** para usar la página de códigos definida para la configuración regional actual (vea la siguiente lista de constantes de manifiesto y resultados de comportamiento de asociados). Para obtener una lista de las rutinas multibyte que dependen de la página de códigos de configuración regional, y no de la página de códigos multibyte, vea [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

La página de códigos multibyte también afecta al procesamiento de caracteres multibyte por las siguientes rutinas de la biblioteca en tiempo de ejecución:

||||
|-|-|-|
|[_exec (funciones)](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Además, todas las rutinas de biblioteca en tiempo de ejecución que reciben los caracteres multibyte *argv* o *envp* argumentos como parámetros de programa (como el **_exec** y **_spawn** familias) procesar estas cadenas en función de la página de códigos multibyte. Por lo tanto, los estas rutinas también se verán afectadas por una llamada a **_setmbcp** que cambia la página de códigos multibyte.

El *codepage* argumento se puede establecer en cualquiera de los siguientes valores:

- **_MB_CP_ANSI** obtenida de página de códigos ANSI de uso del sistema de operativo al inicio del programa.

- **_MB_CP_LOCALE** uso obtenido de página de códigos de la configuración regional actual de una llamada anterior a [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** obtenida de página de códigos OEM del uso del sistema de operativo al inicio del programa.

- **_MB_CP_SBCS** página de códigos de un solo byte de uso. Cuando se establece la página de códigos en **_MB_CP_SBCS**, una rutina como [_ismbblead](ismbblead-ismbblead-l.md) siempre devuelve false.

- Cualquier otro valor válido de página de códigos, independientemente de si el valor es una página de códigos de ANSI, OEM o una página de códigos compatible con otros sistemas operativos (excepto UTF-7 y UTF-8, que no son compatibles).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
