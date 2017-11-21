---
title: 'Comptr:: operator&amp; operador | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator&
dev_langs: C++
helpviewer_keywords: operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2b464a77fedf0d996210040b744faea0ee7372ef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="comptroperatoramp-operator"></a>Comptr&amp; (operador)
Libera la interfaz asociada a esta `ComPtr` objeto y, a continuación, recupera la dirección de la `ComPtr` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Una referencia débil a actual `ComPtr`.  
  
## <a name="remarks"></a>Comentarios  
 Este método difiere de [comptr:: Getaddressof](../windows/comptr-getaddressof-method.md) en que este método libera una referencia al puntero de interfaz. Utilice `ComPtr::GetAddressOf` cuando solicitan la dirección del puntero de interfaz, pero no desea liberar esa interfaz.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)