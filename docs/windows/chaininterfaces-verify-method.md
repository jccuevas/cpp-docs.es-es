---
title: Método Chaininterfaces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a845ea047682fda97ae581f4daad26775241ddf8
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466844"
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify (Método)
Comprueba que cada interfaz definida por los parámetros de plantilla *I0* a través de *I9* hereda de IUnknown y IInspectable y que *I0* hereda *I1* a través de *I9*.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>Comentarios  
 Si se produce un error en la operación de comprobación, un **static_assert** emite un mensaje de error que describe el error.  
  
## <a name="remarks"></a>Comentarios  
 Parámetros de plantilla *I0* y *I1* son necesarios y los parámetros *I2* a través de *I9* son opcionales.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)