---
title: _com_ptr_t::AddRef | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d873d91192dc13f7b1277cbe8ef26b24421b6904
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef
**Específicos de Microsoft**  
  
 Llamadas a la `AddRef` función miembro de **IUnknown** en el puntero de interfaz encapsulado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
void AddRef( );  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Llamadas `IUnknown::AddRef` en el puntero de interfaz encapsulado, cuando se genera un `E_POINTER` error si el puntero es **NULL**.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
