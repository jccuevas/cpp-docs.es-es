---
title: 'Weakref:: operator&amp; operador | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 125ffe998e7c3f225f72e3fb47df4ef3525c37f9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649053"
---
# <a name="weakrefoperatoramp-operator"></a>Weakref:: operator&amp; operador
Devuelve un `ComPtrRef` objeto que representa el actual **WeakRef** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&() throw()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un `ComPtrRef` objeto que representa el actual **WeakRef** objeto.  
  
## <a name="remarks"></a>Comentarios  
 Se trata de un operador de aplicación auxiliar interna que no está pensado para usarse en el código.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [WeakRef (clase)](../windows/weakref-class.md)