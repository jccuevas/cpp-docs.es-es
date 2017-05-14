---
title: feupdateenv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- feupdateenv
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
apitype: HeaderDef
f1_keywords:
- feupdateenv
- fenv/feupdateenv
dev_langs:
- C++
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 0bc689cdf4a76412afd44c88357321cdc0778b40
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="feupdateenv"></a>feupdateenv
Guarda las excepciones de punto flotante generadas actualmente, restaura el estado del entorno de punto flotante especificado y luego genera las excepciones de punto flotante guardadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int feupdateenv(  
   const fenv_t* penv  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `penv`  
 Puntero a un objeto `fenv_t` que contiene un entorno de punto flotante que se establece con una llamada a [fegetenv](fegetenv1.md) o [feholdexcept](feholdexcept2.md). También puede especificar el entorno de punto flotante de inicio predeterminado mediante la macro FE_DFL_ENV.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve 0 si todas las acciones se completan correctamente. De lo contrario, devuelve un valor distinto de cero.  
  
## <a name="remarks"></a>Comentarios  
 La función `feupdateenv` realiza varias acciones. En primer lugar, almacena las marcas de estado de excepción de punto flotante actuales en el almacenamiento automático. Después, establece el entorno actual de punto flotante a partir del valor almacenado en el objeto `fenv_t` al que apunta `penv`. Si `penv` no es FE_DFL_ENV o no apunta a un objeto `fenv_t` válido, el comportamiento posterior es indefinido. Por último, `feupdateenv` genera las excepciones de punto flotante almacenadas localmente.  
  
 Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulte [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado C|Encabezado C++|  
|--------------|--------------|------------------|  
|`feupdateenv`|\<fenv.h>|\<cfenv>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)
