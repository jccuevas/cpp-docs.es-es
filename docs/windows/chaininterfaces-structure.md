---
title: ChainInterfaces (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
dev_langs:
- C++
helpviewer_keywords:
- ChainInterfaces structure
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 18814a4ad87cefa39201d369926c0778931d4d64
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861141"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces (estructura)
Especifica las funciones de comprobación e inicialización que se pueden aplicar a un conjunto de identificadores de interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename I0,  
   typename I1,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct ChainInterfaces : I0;  
template <  
   typename DerivedType,  
   typename BaseType,  
   bool hasImplements,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8,  
   typename I9  
>  
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `I0`  
 (Obligatorio) Id. de interfaz 0.  
  
 `I1`  
 (Obligatorio) Id. de interfaz 1.  
  
 `I2`  
 (Opcional) Id. de interfaz 2.  
  
 `I3`  
 (Opcional) Id. de interfaz 3.  
  
 `I4`  
 (Opcional) Id. de interfaz 4.  
  
 `I5`  
 (Opcional) Id. de interfaz 5.  
  
 `I6`  
 (Opcional) Id. de interfaz 6.  
  
 `I7`  
 (Opcional) Id. de interfaz 7.  
  
 `I8`  
 (Opcional) Id. de interfaz 8.  
  
 `I9`  
 (Opcional) Id. de interfaz 9.  
  
 `DerivedType`  
 Un tipo derivado.  
  
 `BaseType`  
 El tipo base de un tipo derivado.  
  
 `hasImplements`  
 Valor de un valor booleano que si `true`, significa que no se puede usar un [MixIn](../windows/mixin-structure.md) estructura con una clase que no se deriva de la [implementa](../windows/implements-structure.md) estructura.  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ChainInterfaces::CanCastTo (método)](../windows/chaininterfaces-cancastto-method.md)|Indica si el identificador de interfaz especificado se puede convertir a cada una de las especializaciones definidas por los parámetros de plantilla ChainInterface.|  
|[ChainInterfaces::CastToUnknown (método)](../windows/chaininterfaces-casttounknown-method.md)|Convierte el puntero de interfaz del tipo definido por el `I0` parámetro de plantilla a un puntero a IUnknown.|  
|[ChainInterfaces::FillArrayWithIid (método)](../windows/chaininterfaces-fillarraywithiid-method.md)|Almacena el identificador de interfaz definido por el `I0` parámetro de plantilla en una ubicación especificada de una matriz especificada de identificadores de interfaz.|  
|[ChainInterfaces::Verify (método)](../windows/chaininterfaces-verify-method.md)|Comprueba que cada interfaz definido por los parámetros de plantilla `I0` a través de `I9` hereda de IUnknown o IInspectable y que `I0` hereda de `I1` a través de `I9`.|  
  
### <a name="protected-constants"></a>Constantes protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[ChainInterfaces::IidCount (constante)](../windows/chaininterfaces-iidcount-constant.md)|El número total de identificadores contenidos en las interfaces especificadas por los parámetros de plantilla interfaz `I0` a través de `I9`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `I0`  
  
 `ChainInterfaces`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)