---
title: _com_ptr_t::Detach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t::Detach
dev_langs: C++
helpviewer_keywords: Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ddb1d52ab9706293a03be074c3698c35c1bf291c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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