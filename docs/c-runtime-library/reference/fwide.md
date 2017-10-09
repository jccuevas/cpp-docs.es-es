---
title: fwide | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fwide
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
apitype: DLLExport
f1_keywords:
- fwide
dev_langs:
- C++
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: f10bd98a6dedba2181aa1d5ebba60f64dda093be
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fwide"></a>fwide
Sin implementar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int fwide(  
   FILE *stream,  
   int mode;  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stream`  
 Puntero a la estructura `FILE` (se omite).  
  
 `mode`  
 Nuevo ancho de la secuencia: positivo para carácter ancho, negativo para byte, cero para dejarlo sin cambios. (Este valor se omite).  
  
## <a name="return-value"></a>Valor devuelto  
 En este momento, esta función solo devuelve `mode`.  
  
## <a name="remarks"></a>Comentarios  
 La versión actual de esta función no cumple con el estándar.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`fwide`|\<wchar.h>|  
  
 Para obtener más información, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).
