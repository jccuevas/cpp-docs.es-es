---
title: 'Interfacetraits:: Casttobase (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
dev_langs:
- C++
helpviewer_keywords:
- CastToBase method
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8cd8fa2106ac3792c0352aa40ea34b049c1e5ce4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename T>  
static __forceinline Base* CastToBase(  
   _In_ T* ptr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de parámetro `ptr`.  
  
 `ptr`  
 Puntero a un tipo `T`.  
  
## <a name="return-value"></a>Valor devuelto  
 Un puntero a `Base`.  
  
## <a name="remarks"></a>Comentarios  
 Convierte el puntero especificado a un puntero a `Base`.  
  
 Para obtener más información acerca de `Base`, vea la sección de definiciones de tipo público en [InterfaceTraits (estructura)](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [InterfaceTraits (estructura)](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)