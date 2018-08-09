---
title: DerefHelper (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
dev_langs:
- C++
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e5c4965ab8a013fdd52e6dfa51e74bfbf54ed73
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651540"
---
# <a name="derefhelper-structure"></a>DerefHelper (estructura)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <  
   typename T  
>  
struct DerefHelper;  
  
template <  
   typename T  
>  
struct DerefHelper<T*>;  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 Un parámetro de plantilla.  
  
## <a name="remarks"></a>Comentarios  
 Representa un puntero sin referencia a la `T*` parámetro de plantilla.  
  
 **DerefHelper** se utiliza en una expresión como: `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`DerefType`|Identificador del parámetro de plantilla desreferenciado `T*`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `DerefHelper`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)