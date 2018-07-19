---
title: rename_namespace | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a51114787dde2f858a8409538083282ef292d599
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839396"
---
# <a name="renamenamespace"></a>rename_namespace
**Específicos de C++**  
  
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