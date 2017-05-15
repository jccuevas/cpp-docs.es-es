---
title: once_flag (Estructura) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: a39919d3c1608d53edc6a75ecc3dd2e0ff504b1c
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

---
# <a name="onceflag-structure"></a>once_flag (Estructura)
Representa un `struct` que se usa con la función de plantilla [call_once](../standard-library/mutex-functions.md#call_once) para asegurarse de que solo se llame una vez al código de inicialización, incluso ante la presencia de varios subprocesos de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
struct once_flag { constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag& operator=(const once_flag&); };  
  
## <a name="remarks"></a>Comentarios  
 El `once_flag``struct` solo tiene un constructor predeterminado.  
  
 Los objetos de tipo `once_flag` pueden crearse, pero no pueden copiarse.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<mutex >  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




