---
title: _fread_nolock_s2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: _fread_nolock_s
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
- _fread_nolock_s
- stdio/_fread_nolock_s
dev_langs: C++
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a0bec6662cd661ef4a81d66027b272cc297c84fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="freadnolocks"></a>_fread_nolock_s
Lee datos desde una secuencia, sin bloquear otros subprocesos. Esta versión de [fread_nolock](../../c-runtime-library/reference/fread-nolock.md) incluye mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t _fread_nolock_s(   
   void *buffer,  
   size_t bufferSize,  
   size_t elementSize,  
   size_t elementCount,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `buffer`  
 Ubicación de almacenamiento de los datos.  
  
 `bufferSize`  
 Tamaño del búfer de destino en bytes.  
  
 `elementSize`  
 Tamaño del elemento que se va a leer en bytes.  
  
 `elementCount`  
 Número máximo de elementos que se va a leer.  
  
 `stream`  
 Puntero a la estructura `FILE` .  
  
## <a name="return-value"></a>Valor devuelto  
 Consulte [fread_s](../../c-runtime-library/reference/fread-s.md).  
  
## <a name="remarks"></a>Comentarios  
 Esta función es una versión que no es de bloqueo de `fread_s`. Es idéntica a `fread_s` , salvo que no está protegidas contra interferencias de otros subprocesos. Puede ser más rápidas porque no incurre en la sobrecarga de bloquear otros subprocesos. Use esta función solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_fread_nolock_s`|C: \<stdio.h>; C++: \<cstdio> o \<stdio.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [_read](../../c-runtime-library/reference/read.md)