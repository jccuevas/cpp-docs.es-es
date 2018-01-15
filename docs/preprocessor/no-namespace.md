---
title: no_namespace | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_namespace
dev_langs: C++
helpviewer_keywords: no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6b83e60aca7ea0e39ba67834ad1def0896dcdc07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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