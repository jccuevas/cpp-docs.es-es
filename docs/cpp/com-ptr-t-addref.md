---
title: _com_ptr_t::AddRef | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54a1b629f254bae2b72790546bcbb00185f2c44c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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