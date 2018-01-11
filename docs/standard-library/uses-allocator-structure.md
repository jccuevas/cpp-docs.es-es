---
title: uses_allocator (Estructura) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: future/std::uses_allocator
dev_langs: C++
ms.assetid: c418f002-62e9-4806-b70c-41c663cae583
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 049eccb55296530c1c521004455548b1019b7d57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="usesallocator-structure"></a>uses_allocator (Estructura)
Especializaciones que siempre son verdaderas.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty, class Alloc>
struct uses_allocator<promise<Ty>, Alloc> : true_type;
template <class Ty, class Alloc>
struct uses_allocator<packaged_task<Ty>, Alloc> : true_type;
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<futura >  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<future>](../standard-library/future.md)



