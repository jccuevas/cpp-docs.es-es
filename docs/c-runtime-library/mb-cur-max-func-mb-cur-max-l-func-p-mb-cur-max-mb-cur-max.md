---
title: ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
apilocation:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
- __mb_cur_max
dev_langs:
- C++
helpviewer_keywords:
- __mb_cur_max
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
ms.assetid: 60d36108-1ca7-45a6-8ce7-68a91f13e3a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7eb9682a648f8e302a620e3c2e0dc1631abf7945
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068278"
---
# <a name="mbcurmaxfunc-mbcurmaxlfunc-pmbcurmax-mbcurmax"></a>___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max

Función de CRT interna. Recupera el número máximo de bytes en un carácter multibyte de la configuración local actual o especificada.

## <a name="syntax"></a>Sintaxis

```cpp
int ___mb_cur_max_func(void);
int ___mb_cur_max_l_func(_locale_t locale);
int * __p___mb_cur_max(void);
#define __mb_cur_max (___mb_cur_max_func())
```

#### <a name="parameters"></a>Parámetros

locale Estructura de configuración local de la que obtener los resultados. Si este valor es nulo, se usa la configuración regional de subproceso actual.

## <a name="return-value"></a>Valor devuelto

Número máximo de bytes en un carácter multibyte de la configuración local para el subproceso actual o de la configuración local especificada.

## <a name="remarks"></a>Comentarios

Se trata de una función interna que CRT usa para recuperar el valor actual de la macro [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) del almacenamiento local de subprocesos. Le recomendamos usar la macro `MB_CUR_MAX` en su código de cara a la portabilidad.

La macro `__mb_cur_max` constituye una forma muy cómoda de llamar a la función `___mb_cur_max_func()`. La función `__p___mb_cur_max` se define para la compatibilidad con Visual C++ 5.0 y versiones anteriores.

Las funciones de CRT internas son específicas de la implementación y están sujetas a cambio en cada versión. Se desaconseja usarlas en el código.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h>, \<stdlib.h>|

## <a name="see-also"></a>Vea también

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)