---
title: _com_ptr_t::Detach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf38e433f7042707b502a4cba2088db9412adb29
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405839"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach
**Específicos de Microsoft**  
  
 Extrae y devuelve el puntero de interfaz encapsulado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Interface* Detach( ) throw( );  
```  
  
## <a name="remarks"></a>Comentarios  
 Extrae y devuelve el puntero de interfaz encapsulado y, a continuación, borra el almacenamiento del puntero encapsulado en NULL. Esto quita el puntero de interfaz de la encapsulación. Es decisión suya llamar a `Release` en el puntero de interfaz devuelto.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)