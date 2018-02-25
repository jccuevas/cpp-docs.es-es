---
title: raw_interfaces_only | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eff60ded57ae66b43dee4b3b95699ad498fa0358
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**C++ Specific**  
  
 Suprime la generación de funciones de contenedor de control de errores y [propiedad](../cpp/property-cpp.md) declaraciones que usan esas funciones de contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
raw_interfaces_only  
```  
  
## <a name="remarks"></a>Comentarios  
 El atributo `raw_interfaces_only` también hace que se quite el prefijo predeterminado utilizado en la nomenclatura de las funciones que no son de propiedad. Normalmente, el prefijo es **raw_**. Si se especifica este atributo, los nombres de función pertenecen directamente a la biblioteca de tipos.  
  
 Este atributo permite exponer solo el contenido de bajo nivel de la biblioteca de tipos.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)