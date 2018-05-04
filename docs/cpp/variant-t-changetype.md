---
title: _variant_t::ChangeType | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
dev_langs:
- C++
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53fd73fc9606053dda6f8c143618373ad9bb7e4e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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