---
title: '&lt;typeindex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <typeindex>
dev_langs:
- C++
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 4279c10994de9247819e58a06276ef9690b39bb8
ms.lasthandoff: 02/24/2017

---
# <a name="lttypeindexgt"></a>&lt;typeindex&gt;
Incluya el encabezado estándar \<typeindex > para definir una clase y función que admitan la indización de objetos de clase [type_info](../cpp/type-info-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#include <typeindex>  
```  
  
## <a name="remarks"></a>Comentarios  
 La [estructura hash](../standard-library/hash-structure.md) define una `hash function` adecuada para asignar valores de tipo [type_index](../standard-library/type-index-class.md) a una distribución de valores de índice.  
  
 La clase `type_index` encapsula un puntero a un objeto `type_info` para facilitar la indización.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)




