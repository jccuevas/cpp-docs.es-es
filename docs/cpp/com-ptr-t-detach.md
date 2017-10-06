---
title: _com_ptr_t::Detach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
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
ms.openlocfilehash: f61b0fb05f182ef2723fdcc564fd697f490aed20
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach
**Específicos de Microsoft**  
  
 Extrae y devuelve el puntero de interfaz encapsulado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Interface* Detach( ) throw( );  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Extrae y devuelve el puntero de interfaz encapsulado y, a continuación, borra el almacenamiento del puntero encapsulado a **NULL**. Esto quita el puntero de interfaz de la encapsulación. Es decisión suya llamar a **versión** en el puntero de interfaz devuelto.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
