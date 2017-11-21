---
title: _variant_t::ChangeType | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
dev_langs: C++
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8fea359c3f256d56f4d112fe93bb736a16892ea4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType
**Específicos de Microsoft**  
  
 Cambia el tipo de la `_variant_t` objeto para el functoid **VARTYPE**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `vartype`  
 El **VARTYPE** para este `_variant_t` objeto.  
  
 `pSrc`  
 Un puntero al objeto `_variant_t` que se va a convertir. Si este valor es **NULL**, se realiza la conversión en su lugar.  
  
## <a name="remarks"></a>Comentarios  
 Esta función miembro convierte un `_variant_t` objeto en el functoid **VARTYPE**. Si `pSrc` es **NULL**, la conversión se realiza en su lugar, en caso contrario `_variant_t` se copia el objeto de `pSrc` y, a continuación, convertir.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_variant_t (Clase)](../cpp/variant-t-class.md)