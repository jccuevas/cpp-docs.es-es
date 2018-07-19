---
title: _variant_t::ChangeType | Microsoft Docs
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
ms.openlocfilehash: f87d9e4d7193755f70e3463f4da60d88a7bd832c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944445"
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType
**Específicos de Microsoft**  
  
 Cambia el tipo de la `_variant_t` objeto del `VARTYPE`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *VarType*  
 El `VARTYPE` para este `_variant_t` objeto.  
  
 *pSrc*  
 Un puntero al objeto `_variant_t` que se va a convertir. Si este valor es NULL, la conversión se realiza en su lugar.  
  
## <a name="remarks"></a>Comentarios  
 Esta función miembro convierte un `_variant_t` objeto indicado `VARTYPE`. Si *pSrc* es NULL, la conversión se realiza en su lugar, en caso contrario `_variant_t` se copia el objeto de *pSrc* y, a continuación, puede convertir.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_variant_t (Clase)](../cpp/variant-t-class.md)