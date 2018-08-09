---
title: ActivationFactory (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactory class
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 43e4932f93c4b9954343df2aecd4db3b13ebc147
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649210"
---
# <a name="activationfactory-class"></a>ActivationFactory (clase)
Habilita una o más clases que activa Windows Runtime.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;  
```  
  
### <a name="parameters"></a>Parámetros  
 *I0*  
 La interfaz de cero.  
  
 *I1*  
 La primera interfaz.  
  
 *I2*  
 La segunda interfaz.  
  
## <a name="remarks"></a>Comentarios  
 **ActivationFactory** proporciona los métodos de registro y la funcionalidad básica para el `IActivationFactory` interfaz. **ActivationFactory** también le permite proporcionar una implementación de generador personalizado.  
  
 El siguiente fragmento de código simbólicamente ilustra cómo usar ActivationFactory.  
  
 [!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]  
  
 El siguiente fragmento de código muestra cómo usar el [implementa](../windows/implements-structure.md) estructura para especificar más de tres identificadores de interfaz.  
  
 `struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ActivationFactory::ActivationFactory (constructor)](../windows/activationfactory-activationfactory-constructor.md)|Inicializa el **ActivationFactory** clase.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ActivationFactory::AddRef (método)](../windows/activationfactory-addref-method.md)|Incrementa el recuento de referencias del elemento actual **ActivationFactory** objeto.|  
|[ActivationFactory::GetIids (método)](../windows/activationfactory-getiids-method.md)|Recupera una matriz de identificadores de interfaz implementada.|  
|[ActivationFactory::GetRuntimeClassName (método)](../windows/activationfactory-getruntimeclassname-method.md)|Obtiene el nombre de clase en tiempo de ejecución del objeto que actual **ActivationFactory** crea una instancia.|  
|[ActivationFactory::GetTrustLevel (método)](../windows/activationfactory-gettrustlevel-method.md)|Obtiene el nivel de confianza del objeto que actual **ActivationFactory** crea una instancia.|  
|[ActivationFactory::QueryInterface (método)](../windows/activationfactory-queryinterface-method.md)|Recupera un puntero a la interfaz especificada.|  
|[ActivationFactory::Release (método)](../windows/activationfactory-release-method.md)|Disminuye el recuento de referencias del elemento actual **ActivationFactory** objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `ActivationFactory`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)