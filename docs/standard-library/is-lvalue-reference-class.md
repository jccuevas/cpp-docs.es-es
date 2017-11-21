---
title: Clase is_lvalue_reference | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_lvalue_reference
dev_langs: C++
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c150a38604ad2c0f6b00b000c7897ed700c940c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="islvaluereference-class"></a>is_lvalue_reference (Clase)
Comprueba si el tipo es una referencia a un valor L.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty>
struct is_lvalue_reference;
```  
  
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia de este predicado de tipo contiene true si el tipo `Ty` es una referencia a un objeto o una función; de lo contrario, contiene false. Tenga en cuenta que es posible que `Ty` no sea una referencia a un valor R. Para obtener más información sobre rvalues, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)   
 [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)



