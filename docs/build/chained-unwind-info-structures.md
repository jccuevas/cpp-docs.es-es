---
title: Encadenar las estructuras de información de desenredo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87469a381c038462549d20b105b791ddb17b1656
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="chained-unwind-info-structures"></a>Estructuras encadenadas de información de desenredo
Si se establece el indicador UNW_FLAG_CHAININFO, a continuación, una estructura de información de desenredo será secundaria y el campo de dirección controlador/encadenadas de información de la excepción compartida contiene la información de desenredo principal. El código siguiente recupera información, suponiendo que de desenredo de la réplica principal `unwindInfo` es la estructura que tiene el UNW_FLAG_CHAININFO marcador establecido.  
  
```  
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);  
```  
  
 La información encadenada es útil en dos situaciones. En primer lugar, se puede utilizar para segmentos de código no contiguas. Mediante el uso de información encadenada, puede reducir el tamaño de la información de desenredo necesaria, ya que no es necesario que duplicar la matriz de códigos de desenredo de la información de desenredo principal.  
  
 También puede usar información encadenada para agrupar registros variables guardados. El compilador puede retrasar el guardar algunos registros variables hasta que está fuera del prólogo de entrada de función. Puede registrar esto disponiendo de información de desenredo principal para la parte de la función delante del código agrupado y, a continuación, configurar la información encadenada con un tamaño distinto de cero de prólogo, donde los códigos de desenredado de la información encadenada reflejan se han guardado los registros no volátiles. En ese caso, los códigos de desenredado son todas las instancias de UWOP_SAVE_NONVOL. No se admite una agrupación que guarda los registros no volátiles usando un PUSH o modifica el registro RSP mediante una asignación fija adicional de la pila.  
  
 Un elemento UNWIND_INFO con UNW_FLAG_CHAININFO establecido puede contener una entrada RUNTIME_FUNCTION cuyo elemento UNWIND_INFO también tenga UNW_FLAG_CHAININFO establecido (ajuste de reducción múltiple). Finalmente, la información de desenredo encadenada punteros llegarán a un elemento UNWIND_INFO con UNW_FLAG_CHAININFO no activado; Este es el elemento UNWIND_INFO principal, que señala al punto de entrada del procedimiento real.  
  
## <a name="see-also"></a>Vea también  
 [Datos de desenredo para la compatibilidad con el control de excepciones y el depurador](../build/unwind-data-for-exception-handling-debugger-support.md)