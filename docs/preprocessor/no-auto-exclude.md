---
title: no_auto_exclude | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- no_auto_exclude
dev_langs:
- C++
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 492e906b542ee8f378a350b04abfb1ec2e738801
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="noautoexclude"></a>no_auto_exclude
**C++ Specific**  
  
 Deshabilita la exclusión automática.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
no_auto_exclude  
```  
  
## <a name="remarks"></a>Comentarios  
 Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos. `#import` intenta evitar varios errores de definición mediante la exclusión automática de dichos elementos. Cuando esto sucede, [C4192 de advertencia del compilador (nivel 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) se emiten para que cada elemento que se excluirá. Se puede deshabilitar esta exclusión automática con este atributo.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)