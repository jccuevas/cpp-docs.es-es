---
title: no_smart_pointers | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- no_search_pointers
dev_langs:
- C++
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d1e06265771a163375d1095b4c481aa6d7d250f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="nosmartpointers"></a>no_smart_pointers
**C++ Specific**  
  
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