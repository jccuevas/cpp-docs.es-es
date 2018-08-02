---
title: 'Comptr:: operator&amp; operador | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0afff1699a4c7a3a14f07967cfb5ba5727ba0320
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461567"
---
# <a name="comptroperatoramp-operator"></a>Comptr:: operator&amp; operador
Libera la interfaz asociada a este **ComPtr** de objetos y, a continuación, recupera la dirección de la **ComPtr** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Una referencia débil a la actual **ComPtr**.  
  
## <a name="remarks"></a>Comentarios  
 Este método difiere [Getaddressof](../windows/comptr-getaddressof-method.md) en que este método libera una referencia al puntero de interfaz. Use `ComPtr::GetAddressOf` cuando se requiere la dirección del puntero de interfaz, pero no desea liberar esa interfaz.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)