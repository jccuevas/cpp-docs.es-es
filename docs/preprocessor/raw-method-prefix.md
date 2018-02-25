---
title: raw_method_prefix | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- raw_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc80d1468d3ac33bf7506aab98945b9c2e610e51
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="rawmethodprefix"></a>raw_method_prefix
**C++ Specific**  
  
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