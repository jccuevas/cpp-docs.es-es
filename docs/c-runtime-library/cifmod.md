---
title: _CIfmod | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CIfmod
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _CIfmod
- CIfmod
dev_langs:
- C++
helpviewer_keywords:
- CIfmod intrinsic
- _CIfmod intrinsic
ms.assetid: 7c050653-7ec6-4810-b3a7-7a0057ea65ed
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 16654ce580b4ed3b9cf194c60f4f602e4be40540
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="cifmod"></a>_CIfmod
Calcula el resto del punto flotante de los dos valores superiores de la pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __cdecl _CIfmod();  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta versión de la función `fmod` tiene una convención de llamada especializada que el compilador entiende. Acelera la ejecución porque evita que se generen copias y ayuda con la asignación de registros.  
  
 El valor resultante se inserta en la parte superior de la pila.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** x86  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmod, fmodf](../c-runtime-library/reference/fmod-fmodf.md)
