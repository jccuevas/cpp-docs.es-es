---
title: Implementa la estructura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
dev_langs:
- C++
helpviewer_keywords:
- Implements structure
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 31b95901f2c0b7ff210cc8542dce49991a9eef87
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014823"
---
# <a name="implements-structure"></a>Implements (estructura)
Implementa `QueryInterface` y `GetIid` para las interfaces especificadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct __declspec(novtable) Implements : Details::ImplementsHelper<RuntimeClassFlags<WinRt>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT>, Details::ImplementsBase;  
template <  
   int flags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
struct __declspec(novtable) Implements<RuntimeClassFlags<flags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : Details::ImplementsHelper<RuntimeClassFlags<flags>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT>, Details::ImplementsBase;  
```  
  
### <a name="parameters"></a>Parámetros  
 *I0*  
 El identificador de interfaz de cero. (Obligatorio)  
  
 *I1*  
 El primer identificador de interfaz. (Opcional)  
  
 *I2*  
 El segundo identificador de interfaz. (Opcional)  
  
 *I3*  
 El tercer identificador de interfaz. (Opcional)  
  
 *I4*  
 El cuarto identificador de interfaz. (Opcional)  
  
 *I5*  
 El quinto identificador de interfaz. (Opcional)  
  
 *I6*  
 El sexto ID de interfaz. (Opcional)  
  
 *I7*  
 El séptimo ID de interfaz. (Opcional)  
  
 *I8*  
 El identificador de identificador de octava interfaz. (Opcional)  
  
 *I9*  
 El noveno ID de interfaz. (Opcional)  
  
 *flags*  
 Marcas de configuración para la clase. Uno o varios [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) enumeraciones que se especifican en un [RuntimeClassFlags](../windows/runtimeclassflags-structure.md) estructura.  
  
## <a name="remarks"></a>Comentarios  
 Se deriva de la lista de interfaces especificadas e implementa las plantillas de aplicación auxiliar para `QueryInterface` y `GetIid`.  
  
 Cada *I0* a través de *I9* parámetro de interfaz debe derivarse de o `IUnknown`, `IInspectable`, o el [ChainInterfaces](../windows/chaininterfaces-structure.md) plantilla. El *marcas* parámetro determina si el soporte técnico se genera para `IUnknown` o `IInspectable`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`ClassFlags`|Sinónimo de `RuntimeClassFlags<WinRt>`.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Implements::CanCastTo (método)](../windows/implements-cancastto-method.md)|Obtiene un puntero a la interfaz especificada.|  
|[Implements::CastToUnknown (método)](../windows/implements-casttounknown-method.md)|Obtiene un puntero subyacente `IUnknown` interfaz.|  
|[Implements::FillArrayWithIid (método)](../windows/implements-fillarraywithiid-method.md)|Inserta el Id. de interfaz especificado por el parámetro de plantilla actual de cero en el elemento de matriz especificado.|  
  
### <a name="protected-constants"></a>Constantes protegidas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Implements::IidCount (constante)](../windows/implements-iidcount-constant.md)|Contiene el número de identificadores de interfaz implementado.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `ImplementsBase`  
  
 `ImplementsHelper`  
  
 `Implements`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)