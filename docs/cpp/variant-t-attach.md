---
title: _variant_t::Attach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
- VARIANT object, attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 33e21d3bea71c80b8b60df222682fda560fbce9c
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
