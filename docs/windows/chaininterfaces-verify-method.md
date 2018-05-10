---
title: 'Chaininterfaces:: Verify (método) | Documentos de Microsoft'
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
ms.openlocfilehash: c83479434a936f32fb0f7367d8cd02c6676c74e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify (Método)
Comprueba que cada interfaz definido por los parámetros de plantilla `I0` a través de `I9` hereda de IUnknown o IInspectable y que `I0` hereda de `I1` a través de `I9`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>Comentarios  
 Si se produce un error en la operación de comprobación, un `static_assert` emite un mensaje de error que describe el error.  
  
## <a name="remarks"></a>Comentarios  
 Parámetros de plantilla `I0` y `I1` son necesarios y los parámetros `I2` a través de `I9` son opcionales.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)