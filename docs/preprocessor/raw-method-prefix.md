---
title: raw_method_prefix | Microsoft Docs
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
ms.openlocfilehash: fc2a37f587d3b5ac2b695171f5620db6521693d2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439684"
---
# <a name="rawmethodprefix"></a>raw_method_prefix
**Específicos de C++**  
  
Especifica otro prefijo para evitar conflictos de nombres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
raw_method_prefix("Prefix")  
```  
  
### <a name="parameters"></a>Parámetros  
*Prefix*  
El prefijo que se va a usar.  
  
## <a name="remarks"></a>Comentarios  
 
Métodos y propiedades de bajo nivel son expuestos por funciones miembro denominadas con el prefijo predeterminado **raw_** para evitar conflictos con las funciones de miembro alto nivel de control de errores.  
  
> [!NOTE]
> Los efectos de la **raw_method_prefix** atributo no se cambiará por la presencia de la [raw_interfaces_only](#_predir_raw_interfaces_only) atributo. El **raw_method_prefix** siempre tiene prioridad sobre `raw_interfaces_only` especifica un prefijo. Si ambos atributos se usan en la misma `#import` instrucción y, a continuación, el prefijo especificado por el **raw_method_prefix** se usa el atributo.  
  
**FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 
[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)