---
title: push_macro | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.push_macro
- push_macro_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, push_macro
- push_macro pragma
ms.assetid: ac89efc9-afd1-4dfe-bfd1-497229b3e81d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81e41ef7bf7b93e4b2a533dddcb82fee904cb428
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="pushmacro"></a>push_macro
Guarda el valor de la *macro_name* macro en la parte superior de la pila para esta macro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#pragma push_macro("  
macro_name  
")  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Puede recuperar el valor de *macro_name* con **pop_macro**.  
  
 Vea [pop_macro](../preprocessor/pop-macro.md) para obtener un ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)