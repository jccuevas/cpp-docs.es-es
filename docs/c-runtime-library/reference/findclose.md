---
title: _findclose | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _findclose
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _findclose
- findclose
dev_langs:
- C++
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: fcd76f8daec9c90374989a82f4b4b2f85b4cb5c7
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="findclose"></a>_findclose
Cierra el identificador de búsqueda especificado y libera los recursos asociados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _findclose(   
   intptr_t handle   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `handle`  
 Identificador de búsqueda devuelto por una llamada anterior a `_findfirst`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, `_findclose` devuelve 0. En caso contrario, devuelve -1 y establece `errno` a `ENOENT`, que indica que la búsqueda de coincidencias no más archivos se encontró.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_findclose`|\<io.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="see-also"></a>Vea también  
 [Llamadas del sistema](../../c-runtime-library/system-calls.md)   
 [Funciones de búsqueda de nombre de archivo](../../c-runtime-library/filename-search-functions.md)
