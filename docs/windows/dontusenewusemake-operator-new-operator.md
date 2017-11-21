---
title: New (operador) Dontusenewusemake | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs: C++
helpviewer_keywords: operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5424108692bd97bdea890aff85ab7428276dd430
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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