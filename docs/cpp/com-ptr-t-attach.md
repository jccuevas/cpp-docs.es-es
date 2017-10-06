---
title: _com_ptr_t::Attach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
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
ms.openlocfilehash: aa14a5fb0e54971e19de1b46317d768e7fc06a2e
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="comptrtattach"></a>_com_ptr_t::Attach
**Específicos de Microsoft**  
  
 Encapsula un puntero de interfaz sin formato del tipo de este puntero inteligente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      void Attach(  
   Interface* pInterface   
) throw( );  
void Attach(  
   Interface* pInterface,  
   bool fAddRef   
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pInterface`  
 Puntero a interfaz sin formato.  
  
 `fAddRef`  
 Si es **true**, a continuación, `AddRef` se llama. Si es **false**, `_com_ptr_t` objeto toma propiedad del puntero de interfaz sin formato sin llamar a `AddRef`.  
  
## <a name="remarks"></a>Comentarios  
  
-   **Adjuntar (**`pInterface`**)** `AddRef` no se llama.     La propiedad de la interfaz se pasa a este objeto `_com_ptr_t`. **Versión** se llama para disminuir el recuento de referencias para el puntero previamente encapsulado.  
  
-   **Adjuntar (** `pInterface` **,**`fAddRef`**)** si `fAddRef` es **true**, `AddRef` se llama para incrementar la referencia recuento para el puntero de interfaz encapsulado.       Si `fAddRef` es **false**, `_com_ptr_t` objeto toma propiedad del puntero de interfaz sin formato sin llamar a `AddRef`. **Versión** se llama para disminuir el recuento de referencias para el puntero previamente encapsulado.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
