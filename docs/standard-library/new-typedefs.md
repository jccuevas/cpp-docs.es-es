---
title: Definiciones de tipo &lt;new&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
caps.latest.revision: 7
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: e23ea06002dc840997a0e7202f581cd81ef407c5
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="ltnewgt-typedefs"></a>Definiciones de tipo &lt;new&gt;
||  
|-|  
|[new_handler](#new_handler)|  
  
##  <a name="new_handler"></a> new_handler  
 El tipo que apunta a una función que se puede usar como un controlador nuevo.  
  
```
typedef void (*new_handler)();
```  
  
### <a name="remarks"></a>Comentarios  
 Este tipo de función de controlador se llama mediante **operatornew** o `operator new[]` cuando no pueden satisfacer una solicitud de almacenamiento adicional.  
  
### <a name="example"></a>Ejemplo  
  Vea [set_new_handler](../standard-library/new-functions.md#set_new_handler) para obtener un ejemplo que usa `new_handler` como un valor devuelto.  
  
## <a name="see-also"></a>Vea también  
 [\<new>](../standard-library/new.md)




