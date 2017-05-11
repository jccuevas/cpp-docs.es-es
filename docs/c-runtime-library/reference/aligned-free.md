---
title: _aligned_free | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_free
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- aligned_free
- _aligned_free
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
caps.latest.revision: 16
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 8ddc662a1d497a419ebbaf0a93bfbf0ec17b664a
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="alignedfree"></a>_aligned_free
Libera un bloque de memoria que se ha asignado con [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _aligned_free (  
   void *memblock  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `memblock`  
 Puntero al bloque de memoria que se devolvió a las funciones `_aligned_malloc` o `_aligned_offset_malloc`.  
  
## <a name="remarks"></a>Comentarios  
 `_aligned_free` está marcado como `__declspec(noalias)`, lo que significa que se garantiza que la función no modifica las variables globales. Para obtener más información, consulte [noalias](../../cpp/noalias.md).  
  
 Esta función no valida su parámetro, a diferencia de las demás funciones _aligned de CRT. Si `memblock` es un puntero `NULL`, esta función simplemente no lleva a cabo ninguna otra acción. No modifica `errno` ni invoca al controlador de parámetros no válidos. Si se produce un error en la función debido a que no usa funciones _aligned previamente para asignar el bloque de memoria o se produce un error de alineación de memoria debido a algún desastre imprevisto, la función genera un informe de depuración de [_RPT, _RPTF, _RPTW, _RPTFW (Macros)](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_aligned_free`|\<malloc.h>|  
  
## <a name="example"></a>Ejemplo  
 Para obtener más información, consulte [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md).  
  
## <a name="see-also"></a>Vea también  
 [Alineación de datos](../../c-runtime-library/data-alignment.md)
