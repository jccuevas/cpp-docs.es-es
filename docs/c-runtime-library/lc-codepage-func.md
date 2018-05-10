---
title: ___lc_codepage_func | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- ___lc_codepage_func
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
dev_langs:
- C++
helpviewer_keywords:
- ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef848de1219ae86f447ddf67efb8af6b8e184cc4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="lccodepagefunc"></a>___lc_codepage_func
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
 [_get_current_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../c-runtime-library/reference/free-locale.md)