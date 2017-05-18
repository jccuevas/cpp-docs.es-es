---
title: _fread_nolock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fread_nolock
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fread_nolock
- fread_nolock
dev_langs:
- C++
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- fread_nolock function
- _fread_nolock function
- streams [C++], reading data from
ms.assetid: 60e4958b-1097-46f5-a77b-94af5e7dba40
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 2f988855de03457411b2f26d4df112220c370f2a
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="freadnolock"></a>_fread_nolock
Lee datos desde una secuencia, sin bloquear otros subprocesos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t _fread_nolock(   
   void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `buffer`  
 Ubicación de almacenamiento de los datos.  
  
 `size`  
 Tamaño del elemento en bytes.  
  
 `count`  
 Número máximo de elementos que se va a leer.  
  
 `stream`  
 Puntero a la estructura de `FILE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Consulte [fread](../../c-runtime-library/reference/fread.md).  
  
## <a name="remarks"></a>Comentarios  
 Esta función es una versión que no es de bloqueo de `fread`. Es idéntica a `fread`, salvo que no está protegida contra interferencias de otros subprocesos. Puede ser más rápidas porque no incurre en la sobrecarga de bloquear otros subprocesos. Use esta función solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_fread_nolock`|\<stdio.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [_read](../../c-runtime-library/reference/read.md)
