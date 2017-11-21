---
title: _variant_t::Attach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs: C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 893cf8c10fce70645fa42373f08e6b4636e41d11
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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