---
title: 'Modulebase:: Incrementobjectcount (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
dev_langs:
- C++
helpviewer_keywords:
- IncrementObjectCount method
ms.assetid: 2d70b472-684c-4bb7-8bab-09505cfcaf28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b0e0fd6ecfd4d30dd4921c99d873c23b533ee24
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875479"
---
# <a name="modulebaseincrementobjectcount-method"></a>ModuleBase::IncrementObjectCount (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
virtual long IncrementObjectCount() = 0;  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El recuento antes de la operación de incremento.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se implementa, incrementa el número de objetos que se hace un seguimiento mediante el módulo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [ModuleBase (clase)](../windows/modulebase-class.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)