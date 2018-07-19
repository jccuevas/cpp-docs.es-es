---
title: no_namespace | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_namespace
dev_langs:
- C++
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3d4558b0fd6a4014bc9601d5260882af444f87e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912750"
---
# <a name="nonamespace"></a>no_namespace
**Específicos de C++**  
  
 Especifica que el compilador no genera el espacio de nombres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
no_namespace  
```  
  
## <a name="remarks"></a>Comentarios  
 El contenido de la biblioteca de tipos en el archivo de encabezado `#import` se define normalmente en un espacio de nombres. El espacio de nombres se especifica en el **biblioteca** instrucción del archivo IDL original. Si se especifica el atributo `no_namespace`, el compilador no genera este espacio de nombres.  
  
 Si desea utilizar un nombre de espacio de nombres diferente, a continuación, utilice la [rename_namespace](../preprocessor/rename-namespace.md) atributo en su lugar.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)