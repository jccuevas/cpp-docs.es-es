---
title: raw_method_prefix | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 236c9042393e4ff3de57bea83ad566c8b74d5d3b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839925"
---
# <a name="rawmethodprefix"></a>raw_method_prefix
**Específicos de C++**  
  
 Especifica otro prefijo para evitar conflictos de nombres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
raw_method_prefix("Prefix")  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Prefix`  
 El prefijo que se va a usar.  
  
## <a name="remarks"></a>Comentarios  
 Propiedades de bajo nivel y los métodos expuestos por funciones miembro denominadas con un prefijo predeterminado de **raw_** para evitar conflictos de nombres con las funciones de miembro alto nivel de control de errores.  
  
> [!NOTE]
>  Los efectos de la `raw_method_prefix` atributo no se cambiarán por la presencia de la [raw_interfaces_only](#_predir_raw_interfaces_only) atributo. `raw_method_prefix` tiene siempre prioridad sobre `raw_interfaces_only` cuando se especifica un prefijo. Si ambos atributos se utilizan en la misma instrucción `#import`, se usa el prefijo especificado por el atributo `raw_method_prefix`.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)