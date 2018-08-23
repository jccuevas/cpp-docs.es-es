---
title: optimizar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8222d909ad23157b4e3ed32a6920abadd77709b6
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538703"
---
# <a name="optimize"></a>optimize
Especifica las optimizaciones que se efectuarán función por función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## <a name="remarks"></a>Comentarios  

El **optimizar** pragma debe aparecer fuera de una función y tiene efecto en la primera función definida después de la pragma. El *en* y *desactivar* argumentos activar las opciones especificadas en el *optimization-list* activado o desactivado.  
  
El *optimization-list* puede ser cero o más de los parámetros mostrados en la tabla siguiente.  
  
### <a name="parameters-of-the-optimize-pragma"></a>Parámetros de la directiva pragma optimize  
  
|Parámetros|Tipo de optimización|  
|--------------------|--------------------------|  
|*g*|Habilitar optimizaciones globales.|  
|*s* o *t*|Especificar secuencias cortas o rápidas de código máquina.|  
|*y*|Generar punteros de marco en la pila del programa.|  
  
Estas son las mismas letras usadas con la [/O](../build/reference/o-options-optimize-code.md) opciones del compilador. Por ejemplo, la directiva pragma siguiente es equivalente a la opción del compilador `/Os`:  
  
```  
#pragma optimize( "ts", on )  
```  
  
Mediante el **optimizar** pragma con la cadena vacía (**""**) es una forma especial de la directiva:  
  
Cuando se usa el *desactivar* parámetro, desactiva las optimizaciones, enumeradas en la tabla anterior de este tema, desactivado.  
  
Cuando se usa el *en* parámetro, restablece las optimizaciones a aquellas que especificó con el [/O](../build/reference/o-options-optimize-code.md) opción del compilador.  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## <a name="see-also"></a>Vea también  
 
[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)