---
title: _variant_t::SetString | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
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
ms.openlocfilehash: 0e3502a83b93e89744e280cf9c01aa2d08b09a7e
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="varianttsetstring"></a>_variant_t::SetString
**Específicos de Microsoft**  
  
 Asigna una cadena a este objeto `_variant_t`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      void SetString(  
   const char* pSrc   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pSrc`  
 Puntero a la cadena de caracteres.  
  
## <a name="remarks"></a>Comentarios  
 Convierte una cadena de caracteres ANSI en una cadena `BSTR` Unicode y la asigna a este objeto `_variant_t`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_variant_t (Clase)](../cpp/variant-t-class.md)
