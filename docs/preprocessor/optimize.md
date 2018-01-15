---
title: optimizar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 35b5147b3561df409906af9134ae4ec921a7d16b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="optimize"></a>optimize
Especifica las optimizaciones que se efectuarán función por función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## <a name="remarks"></a>Comentarios  
 El **optimizar** pragma debe aparecer fuera de una función y tiene efecto en la primera función definida después de que la pragma. El **en** y **desactivar** argumentos activar opciones especificadas en el *lista de optimizaciones* activado o desactivado.  
  
 El *lista de optimizaciones* puede ser cero o más de los parámetros mostrados en la tabla siguiente.  
  
### <a name="parameters-of-the-optimize-pragma"></a>Parámetros de la directiva pragma optimize  
  
|Parámetros|Tipo de optimización|  
|--------------------|--------------------------|  
|**g**|Habilitar optimizaciones globales.|  
|**s** o **t**|Especificar secuencias cortas o rápidas de código máquina.|  
|**y**|Generar punteros de marco en la pila del programa.|  
  
 Estas son las mismas letras usadas con la [/O](../build/reference/o-options-optimize-code.md) opciones del compilador. Por ejemplo, la directiva pragma siguiente es equivalente a la **/Os** opción del compilador:  
  
```  
#pragma optimize( "ts", on )  
```  
  
 Mediante el **optimizar** pragma con la cadena vacía (**""**) es una forma especial de la directiva:  
  
 Cuando se usa el **desactivar** parámetro, desactiva las optimizaciones, enumeradas en la tabla anterior de este tema, off.  
  
 Cuando se usa el **en** parámetro, restablece las optimizaciones a las que ha especificado con el [/O](../build/reference/o-options-optimize-code.md) opción del compilador.  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)