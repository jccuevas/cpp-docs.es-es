---
title: alignment_of (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::alignment_of
dev_langs: C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e20d01c50ea743f62c1cca9e45eedd86a5d4b8c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="alignmentof-class"></a>alignment_of (Clase)
Obtiene una alineación del tipo especificado. Este struct se implementa en términos de [alignof](../cpp/alignof-and-alignas-cpp.md). Use `alignof` directamente cuando solo sea necesario consultar un valor de alineación. Use alignment_of cuando necesite una constante integral, por ejemplo, al realizar un envío de etiquetas.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty>
struct alignment_of;
```  
  
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 La consulta de tipo contiene el valor de la alineación del tipo `Ty`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)   
 [aligned_storage (Clase)](../standard-library/aligned-storage-class.md)