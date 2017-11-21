---
title: _variant_t::Detach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
dev_langs: C++
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 014de597ffbc9a7004f821393902ffe05ac1f278
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="varianttdetach"></a>_variant_t::Detach
**Específicos de Microsoft**  
  
 Desasocia el objeto encapsulado **VARIANT** objeto desde este `_variant_t` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
VARIANT Detach( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El objeto encapsulado **VARIANT**.  
  
## <a name="remarks"></a>Comentarios  
 Extrae y devuelve el objeto encapsulado **VARIANT**, a continuación, borra este `_variant_t` objeto sin destruirlo. Esta función miembro quita el **VARIANT** de encapsulación y establece el **VARTYPE** de este `_variant_t` el objeto a `VT_EMPTY`. Depende de usted para liberar el valor devuelto **VARIANT** mediante una llamada a la [VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835) función.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_variant_t (Clase)](../cpp/variant-t-class.md)