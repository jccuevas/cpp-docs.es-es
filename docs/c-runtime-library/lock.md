---
title: _lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _lock
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- lock
- _lock
dev_langs:
- C++
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9a518402d027ae128fcf403752fafb448461628
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="lock"></a>_lock
Adquiere un bloqueo multiproceso.  
  
> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __cdecl _lock  
   int locknum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `locknum`  
 El identificador del bloqueo que se adquirirá.  
  
## <a name="remarks"></a>Comentarios  
 Si ya se adquirió el bloqueo, este método obtiene el bloqueo de todas formas y produce un error interno en tiempo de ejecución de C (CRT). Si el método no puede adquirir un bloqueo, se cierra con un error irrecuperable y establece el código de error en `_RT_LOCK`.  
  
## <a name="requirements"></a>Requisitos  
 **Origen:** mlock.c  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_unlock](../c-runtime-library/unlock.md)