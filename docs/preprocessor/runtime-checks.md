---
title: runtime_checks | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
dev_langs: C++
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7bc333e539ba67b2a999bbeb5a08b9002da4e1fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="runtimechecks"></a>runtime_checks
Deshabilita o restaura la configuración de [/RTC](../build/reference/rtc-run-time-error-checks.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#pragma runtime_checks( "[runtime_checks]", {restore | off} )  
```  
  
## <a name="remarks"></a>Comentarios  
 No se puede habilitar una comprobación en tiempo de ejecución que no se haya habilitado con una opción del compilador. Por ejemplo, si no se especifica /RTC, especificar `#pragma runtime_checks( "s", restore)` no habilitará la comprobación del marco de pila.  
  
 La directiva pragma **runtime_checks** debe aparecer fuera de una función y tiene efecto en la primera función definida después de que se vea la directiva pragma. Los argumentos **restore** y **off** activan o desactivan las opciones especificadas en *runtime_checks* .  
  
 Los parámetros *runtime_checks* pueden ser varios o ninguno de los mostrados en la tabla siguiente.  
  
### <a name="parameters-of-the-runtimechecks-pragma"></a>Parámetros de la directiva pragma runtime_checks  
  
|Parámetros|Tipo de comprobación en tiempo de ejecución|  
|--------------------|-----------------------------|  
|**s**|Habilita la comprobación de pila (marco).|  
|**c**|Comunica los casos en que se asigna un valor a un tipo de datos más pequeño y se provoca una pérdida de datos.|  
|**u**|Comunica cuando se usa una variable antes de definirla.|  
  
 Son las mismas letras usadas con la opción del compilador /RTC. Por ejemplo:  
  
```  
#pragma runtime_checks( "sc", restore )  
```  
  
 El uso de la directiva pragma **runtime_checks** con la cadena vacía (**""**) es una forma especial de la directiva:  
  
-   Cuando se usa el parámetro **off** , desactiva las comprobaciones de errores en tiempo de ejecución, que se enumeran en la tabla anterior.  
  
-   Cuando se usa el parámetro **restore** , restablece las comprobaciones de errores en tiempo de ejecución a las especificadas con la opción del compilador /RTC.  
  
```  
#pragma runtime_checks( "", off )  
.  
.  
.  
#pragma runtime_checks( "", restore )   
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
