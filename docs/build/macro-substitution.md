---
title: "Sustitución de macros | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c2ea7a2509e58cfd4da163cc76c018d06c244fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="macro-substitution"></a>Sustitución de macros
Cuando *Nombredelamacro* se invoca, cada aparición de *string1* en su definición de la cadena se reemplaza por *string2*.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
$(macroname:string1=string2)  
```  
  
## <a name="remarks"></a>Comentarios  
 Sustitución de macros distingue mayúsculas de minúsculas y es literal; *string1* y *string2* no se puede llamar a macros. Sustitución no modifica la definición original. Puede sustituir texto en cualquier macro predefinida excepto [ $$@ ](../build/filename-macros.md).  
  
 No hay espacios ni tabulaciones preceden a los dos puntos; los caracteres situados detrás del signo de dos puntos se interpretan como literales. Si *string2* es null, todas las apariciones de *string1* se eliminan de la cadena de definición de la macro.  
  
## <a name="see-also"></a>Vea también  
 [Uso de una macro NMAKE](../build/using-an-nmake-macro.md)