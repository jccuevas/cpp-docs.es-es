---
title: ___lc_locale_name_func | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- ___lc_locale_name_func
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- ___lc_locale_name_func
dev_langs:
- C++
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a88a518483e9ea668b98b054453e7f449e99048b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="lclocalenamefunc"></a>___lc_locale_name_func
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
 [_get_current_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../c-runtime-library/reference/free-locale.md)