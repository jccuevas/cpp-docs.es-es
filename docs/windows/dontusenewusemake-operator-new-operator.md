---
title: New (operador) Dontusenewusemake | Documentos de Microsoft
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
ms.openlocfilehash: 9785ea27c79ff0a118ff3697a22804c520b265ee
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873685"
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new (Operador)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `__unnamed0`  
 Un parámetro sin nombre que especifica el número de bytes de memoria para asignar.  
  
 `placement`  
 El tipo que se asignará.  
  
## <a name="return-value"></a>Valor devuelto  
 Proporciona una manera de pasar argumentos adicionales si se sobrecarga el operador `new`.  
  
## <a name="remarks"></a>Comentarios  
 Sobrecargas de operador `new` e impide que se usa en RuntimeClass.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [DontUseNewUseMake (clase)](../windows/dontusenewusemake-class.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)