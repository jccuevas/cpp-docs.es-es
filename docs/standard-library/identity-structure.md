---
title: Estructura identity | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- utility/std::identity
- identity
dev_langs:
- C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
caps.latest.revision: 15
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: a7404d2c1a785fd66489421fd7b9689260e0986d
ms.lasthandoff: 02/24/2017

---
# <a name="identity-structure"></a>identity (Estructura)
Estructura que proporciona una definición de tipo como parámetro de plantilla.  
  
## <a name="syntax"></a>Sintaxis  
```  
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
   };  
```  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|Valor que se va a identificar.|  
  
## <a name="remarks"></a>Comentarios  
 La clase contiene la definición de tipo público `type`, que es igual que el tipo de parámetro de plantilla. Se usa junto con la función de plantilla [forward](../standard-library/utility-functions.md#forward) para asegurarse de que un parámetro de función tiene el tipo deseado.  
  
 Para garantizar la compatibilidad con código antiguo, la clase también define la función identity `operator()` que devuelve su argumento `left`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<utility>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [\<utility>](../standard-library/utility.md)




