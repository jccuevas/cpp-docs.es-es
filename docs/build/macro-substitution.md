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
ms.openlocfilehash: d8e63e071629c2647ccd8f89095fbc7c2285f1a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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