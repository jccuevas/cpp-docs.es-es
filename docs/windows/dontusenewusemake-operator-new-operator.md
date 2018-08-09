---
title: Operador new Dontusenewusemake | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b849c7578b29a3d4595a9ecd07c4339dc751e9dd
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652954"
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new (Operador)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *__unnamed0*  
 Un parámetro sin nombre que especifica el número de bytes de memoria para asignar.  
  
 *selección de ubicación*  
 El tipo de asignación.  
  
## <a name="return-value"></a>Valor devuelto  
 Proporciona una forma de pasar argumentos adicionales si se sobrecarga el operador **nuevo**.  
  
## <a name="remarks"></a>Comentarios  
 Las sobrecargas de operador **nueva** e impide que se usa en `RuntimeClass`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [DontUseNewUseMake (clase)](../windows/dontusenewusemake-class.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)