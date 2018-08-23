---
title: no_namespace | Microsoft Docs
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
ms.openlocfilehash: 6eded6b4d543248cc7bf53a0e4ba622b2b74c8b3
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538898"
---
# <a name="nonamespace"></a>no_namespace
**Específicos de C++**  
  
Especifica que el compilador no genera el espacio de nombres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
no_namespace  
```  
  
## <a name="remarks"></a>Comentarios  
 
El contenido de la biblioteca de tipos en el archivo de encabezado `#import` se define normalmente en un espacio de nombres. El espacio de nombres se especifica en el `library` instrucción del archivo IDL original. Si el **no_namespace** atributo se especifica, el compilador no genera este espacio de nombres.  
  
Si desea usar un nombre de espacio de nombres diferente, a continuación, utilice el [rename_namespace](../preprocessor/rename-namespace.md) atributo en su lugar.  
  
**FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 
[atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
[directiva #import](../preprocessor/hash-import-directive-cpp.md)