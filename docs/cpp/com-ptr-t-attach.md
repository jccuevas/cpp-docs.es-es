---
title: _com_ptr_t::Attach | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d8b9eac88c9387c6aeedd140159bb24482c829dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
-   **Adjuntar (**`pInterface`**)** `AddRef` no se llama. La propiedad de la interfaz se pasa a este objeto `_com_ptr_t`. **Versión** se llama para disminuir el recuento de referencias para el puntero previamente encapsulado.  
  
-   **Adjuntar (** `pInterface` **,**`fAddRef`**)** si `fAddRef` es **true**, `AddRef` se llama para incrementar la referencia recuento para el puntero de interfaz encapsulado. Si `fAddRef` es **false**, `_com_ptr_t` objeto toma propiedad del puntero de interfaz sin formato sin llamar a `AddRef`. **Versión** se llama para disminuir el recuento de referencias para el puntero previamente encapsulado.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)