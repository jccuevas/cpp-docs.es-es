---
title: include() | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: include()
dev_langs: C++
helpviewer_keywords: include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 794152aa30c57f22bc611ef758af23b2f205b7b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="include"></a>include()
**Específicos de C++**  
  
 Deshabilita la exclusión automática.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Name1`  
 Primer elemento que se incluirá forzosamente.  
  
 `Name2`  
 Segundo elemento que se incluirá forzosamente (si es necesario).  
  
## <a name="remarks"></a>Comentarios  
 Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos. `#import` intenta evitar varios errores de definición mediante la exclusión automática de dichos elementos. Si los elementos se han excluido, como se indica por [C4192 de advertencia del compilador (nivel 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), y que no deberían tener estado, este atributo se puede usar para deshabilitar la exclusión automática. Este atributo puede tomar cualquier número de argumentos, siendo cada uno el nombre del elemento de la biblioteca de tipos que se incluirá.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)