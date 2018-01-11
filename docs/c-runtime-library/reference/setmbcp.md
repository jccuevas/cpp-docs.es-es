---
title: _setmbcp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _setmbcp
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
dev_langs: C++
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b09953ffdb1523078f31cad08d53253b9d79892
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="setmbcp"></a>_setmbcp
Establece una nueva página de códigos multibyte.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _setmbcp(  
   int codepage   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `codepage`  
 Nueva configuración de la página de códigos para las rutinas multibyte independientes de la configuración regional.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve 0 si la página de códigos se establece correctamente. Si se proporciona un valor de la página de códigos no válida para `codepage`, devuelve -1 y la configuración de la página de código se ha modificado. Establece `errno` en `EINVAL` si se produce un error de asignación de memoria.  
  
## <a name="remarks"></a>Comentarios  
 La función `_setmbcp` especifica una nueva página de códigos multibyte. De forma predeterminada, el sistema en tiempo de ejecución establece automáticamente la página de códigos multibyte en la página de códigos ANSI predeterminada del sistema. La configuración de la página de códigos multibyte afecta a todas las rutinas multibyte que no dependen de la configuración regional. Sin embargo, se puede indicar a `_setmbcp` que use la página de códigos definida para la configuración regional actual (consulte la siguiente lista de constantes de manifiesto y los resultados de comportamiento asociados). Para obtener una lista de las rutinas multibyte que dependen de la página de códigos de configuración regional, y no de la página de códigos multibyte, vea [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).  
  
 La página de códigos multibyte también afecta al procesamiento de caracteres multibyte por las siguientes rutinas de la biblioteca en tiempo de ejecución:  
  
||||  
|-|-|-|  
|[_exec (funciones)](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](../../c-runtime-library/reference/mktemp-wmktemp.md)|[_stat](../../c-runtime-library/reference/stat-functions.md)|  
|[_fullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)|[_spawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[_makepath](../../c-runtime-library/reference/makepath-wmakepath.md)|[_splitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)|[tmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
  
 Además, todas las rutinas de la biblioteca en tiempo de ejecución que reciben los argumentos de programa `argv` o `envp` de los caracteres multibyte como parámetros (como las familias `_exec` y `_spawn`) procesan estas cadenas según la página de códigos multibyte. Por lo tanto, estas rutinas también se ven afectadas por una llamada a `_setmbcp` que cambia la página de códigos multibyte.  
  
 El argumento `codepage` se puede establecer en cualquiera de los siguientes valores:  
  
-   `_MB_CP_ANSI` Use la página de códigos de ANSI obtenida por el sistema operativo al iniciar el programa.  
  
-   `_MB_CP_LOCALE` Use la página de códigos de la configuración regional actual obtenida por una llamada anterior a [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
-   `_MB_CP_OEM` Use la página de códigos de OEM obtenida por el sistema operativo al iniciar el programa.  
  
-   `_MB_CP_SBCS` Use la página de códigos de un solo byte. Cuando la página de códigos se establece en `_MB_CP_SBCS`, una rutina como [_ismbblead](../../c-runtime-library/reference/ismbblead-ismbblead-l.md) siempre devuelve false.  
  
-   Cualquier otro valor válido de página de códigos, independientemente de si el valor es una página de códigos de ANSI, OEM o una página de códigos compatible con otros sistemas operativos (excepto UTF-7 y UTF-8, que no son compatibles).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_setmbcp`|\<mbctype.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)