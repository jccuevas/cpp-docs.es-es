---
title: _variant_t::SetString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 090fd7ed027738ebe7bc9276e3b3f124b9212c4a
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463472"
---
# <a name="varianttsetstring"></a>_variant_t::SetString
**Específicos de Microsoft**  
  
 Asigna una cadena a este objeto `_variant_t`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void SetString(const char* pSrc);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pSrc*  
 Puntero a la cadena de caracteres.  
  
## <a name="remarks"></a>Comentarios  
 Convierte una cadena de caracteres ANSI en una cadena `BSTR` Unicode y la asigna a este objeto `_variant_t`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_variant_t (Clase)](../cpp/variant-t-class.md)