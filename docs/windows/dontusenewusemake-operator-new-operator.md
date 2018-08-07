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
ms.openlocfilehash: 59354062dded7792dca1cd84683bba64f6a64aa0
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571430"
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new (Operador)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
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