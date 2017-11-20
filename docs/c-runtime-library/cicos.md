---
title: _CIcos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIcos
apilocation:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- CIcos
- _CIcos
dev_langs: C++
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cab375ac2224ff4c3dfc8f66f84b69a5256f388f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cicos"></a>_CIcos
Calcula el coseno del valor superior de la pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __cdecl _CIcos();  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta versión de la función `cos` tiene una convención de llamada especializada que el compilador entiende. Acelera la ejecución porque evita que se generen copias y ayuda con la asignación de registros.  
  
 El valor resultante se inserta en la parte superior de la pila.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** x86  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)