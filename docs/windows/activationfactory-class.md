---
title: ActivationFactory (clase) | Documentos de Microsoft
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
ms.openlocfilehash: 6775e9466ed337a070b6a234a4d65bb949a009e4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857960"
---
# <a name="activationfactory-class"></a>ActivationFactory (clase)
Habilita una o más clases que activa Windows Runtime.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `I0`  
 La interfaz de cero.  
  
 `I1`  
 La primera interfaz.  
  
 `I2`  
 La segunda interfaz.  
  
## <a name="remarks"></a>Comentarios  
 ActivationFactory proporciona los métodos de registro y la funcionalidad básica para la interfaz IActivationFactory. ActivationFactory también le permite proporcionar una implementación de generador personalizado.  
  
 Simbólicamente, el fragmento de código siguiente muestra cómo utilizar ActivationFactory.  
  
 [!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]  
  
 El siguiente fragmento de código muestra cómo utilizar el [implementa](../windows/implements-structure.md) estructura para especificar más de tres identificadores de interfaz.  
  
 `struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ActivationFactory::ActivationFactory (constructor)](../windows/activationfactory-activationfactory-constructor.md)|Inicializa la clase ActivationFactory.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ActivationFactory::AddRef (método)](../windows/activationfactory-addref-method.md)|Incrementa el recuento de referencias del objeto ActivationFactory actual.|  
|[ActivationFactory::GetIids (método)](../windows/activationfactory-getiids-method.md)|Recupera una matriz de identificadores de interfaz implementado.|  
|[ActivationFactory::GetRuntimeClassName (método)](../windows/activationfactory-getruntimeclassname-method.md)|Obtiene el nombre de clase en tiempo de ejecución del objeto que se crea una instancia de la ActivationFactory actual.|  
|[ActivationFactory::GetTrustLevel (método)](../windows/activationfactory-gettrustlevel-method.md)|Obtiene el nivel de confianza del objeto que se crea una instancia de la ActivationFactory actual.|  
|[ActivationFactory::QueryInterface (método)](../windows/activationfactory-queryinterface-method.md)|Recupera un puntero a la interfaz especificada.|  
|[ActivationFactory::Release (método)](../windows/activationfactory-release-method.md)|Disminuye el recuento de referencias del objeto ActivationFactory actual.|  
  
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