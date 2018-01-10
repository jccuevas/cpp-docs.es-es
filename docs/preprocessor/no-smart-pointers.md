---
title: no_smart_pointers | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_search_pointers
dev_langs: C++
helpviewer_keywords: no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: efa69bf3b0ae770bcd4a29c7430b5b21677b453e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nosmartpointers"></a>no_smart_pointers
**Específicos de C++**  
  
 Suprime la creación de punteros inteligentes para todas las interfaces en la biblioteca de tipos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
no_smart_pointers  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, cuando se utiliza `#import`, se obtiene una declaración de puntero inteligente para todas las interfaces de la biblioteca de tipos. Estos punteros inteligentes son del tipo [clase _com_ptr_t](../cpp/com-ptr-t-class.md).  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)