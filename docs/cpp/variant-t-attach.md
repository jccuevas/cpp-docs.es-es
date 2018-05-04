---
title: _variant_t::Attach | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93c4ec0b4d25f1ca0ec03d9aae1dd9e1c16b79a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="varianttattach"></a>_variant_t::Attach
**Específicos de Microsoft**  
  
 Asocia un **VARIANT** objeto en el `_variant_t` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      void Attach(  
   VARIANT& varSrc   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *varSrc*  
 A **VARIANT** objeto que se adjuntará a este `_variant_t` objeto.  
  
## <a name="remarks"></a>Comentarios  
 Toma posesión de la **VARIANT** encapsulándolo. Esta función miembro libera cualquier encapsulado existente **VARIANT**, a continuación, copia proporcionado **VARIANT**y establece su **VARTYPE** a `VT_EMPTY` para asegurarse de que su solo se pueden liberar los recursos mediante el `_variant_t` destructor.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_variant_t (Clase)](../cpp/variant-t-class.md)