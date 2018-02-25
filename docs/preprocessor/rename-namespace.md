---
title: rename_namespace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37b2c01479cb489f7ed573f55a48f5807161bf63
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="renamenamespace"></a>rename_namespace
**C++ Specific**  
  
 Cambia el espacio de nombres que incluye el contenido de la biblioteca de tipos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
rename_namespace("NewName")  
```  
  
#### <a name="parameters"></a>Parámetros  
 `NewName`  
 Nuevo nombre del espacio de nombres.  
  
## <a name="remarks"></a>Comentarios  
 Toma un único argumento, *NewName*, que especifica el nuevo nombre para el espacio de nombres.  
  
 Para quitar el espacio de nombres, use el [no_namespace](../preprocessor/no-namespace.md) atributo en su lugar.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)