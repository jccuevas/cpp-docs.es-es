---
title: conditional (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::conditional
dev_langs: C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 08c0428f5ed82c0890cdbcbb051f128c52281ce7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="conditional-class"></a>conditional (Clase)
Selecciona uno de dos tipos en función de la condición especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <bool B, class T1, class T2>  
struct conditional;

template <bool _Test, class _T1, class _T2>  
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```  
  
#### <a name="parameters"></a>Parámetros  
 `B`  
 Valor que determina el tipo seleccionado.  
  
 `T1`  
 Resultado del tipo cuando B es true.  
  
 `T2`  
 Resultado del tipo cuando B es false.  
  
## <a name="remarks"></a>Comentarios  
 La definición de tipo de miembro de plantilla `conditional<B, T1, T2>::type` se evalúa como `T1` cuando `B` se evalúa como `true`, y se evalúa como `T2` cuando `B` se evalúa como `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)



