---
title: offsetof Macro | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
- offsetof
dev_langs:
- C++
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a70bb2823f29caf3f76224bfb91c3c9642bbdcf1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="offsetof-macro"></a>offsetof (Macro)
Recupera el desplazamiento de un miembro desde el principio de su estructura primaria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      size_t offsetof(  
   structName,  
   memberName   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *structName*  
 Nombre de la estructura de datos primaria.  
  
 `memberName`  
 Nombre del miembro de la estructura de datos primaria cuyo desplazamiento se determina.  
  
## <a name="return-value"></a>Valor devuelto  
 `offsetof` devuelve el desplazamiento en bytes del miembro especificado desde el principio de su estructura de datos primaria. No se define para campos de bits.  
  
## <a name="remarks"></a>Comentarios  
 La `offsetof` macro devuelve el desplazamiento en bytes de `memberName` desde el principio de la estructura especificada por *structName* como valor de tipo `size_t`. Puede especificar tipos con la palabra clave `struct`.  
  
> [!NOTE]
>  `offsetof` no es una función y no se puede describir mediante un prototipo de C.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`offsetof`|\<stddef.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)