---
title: _abnormal_termination | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _abnormal_termination
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _abnormal_termination
dev_langs:
- C++
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f70520b60ccfaf1af5b223bcb4ea1a90639aa484
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385558"
---
# <a name="abnormaltermination"></a>_abnormal_termination
Indica si el bloque `__finally` de una [instrucción try-finally](../cpp/try-finally-statement.md) se especifica mientras el sistema ejecuta una lista interna de controladores de terminación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
int   _abnormal_termination(  
   );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 `true` si el sistema *desenreda* la pila; en caso contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
 Se trata de una función interna que se usa para administrar las excepciones de desenredado y no está pensada para que se llame desde el código de usuario.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|_abnormal_termination|excpt.h|  
  
## <a name="see-also"></a>Vea también  
 [try-finally (Instrucción)](../cpp/try-finally-statement.md)