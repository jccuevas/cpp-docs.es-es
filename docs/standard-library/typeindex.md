---
title: '&lt;typeindex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <typeindex>
dev_langs:
- C++
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f758ce1d0bce0292be59bdc1af078af156ac20a4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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



