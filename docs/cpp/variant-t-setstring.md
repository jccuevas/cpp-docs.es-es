---
title: _variant_t::SetString | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _variant_t::SetString
dev_langs: C++
helpviewer_keywords: SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fc0fd027bbb4a1049e46351a8a544dac8c5a47aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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