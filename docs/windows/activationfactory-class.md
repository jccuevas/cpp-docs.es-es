---
title: ActivationFactory (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ActivationFactory
dev_langs: C++
helpviewer_keywords: ActivationFactory class
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6876fb3d418a4dac8a68449da5d0eae855daa440
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[ActivationFactory::ActivationFactory (constructor)](../windows/activationfactory-activationfactory-constructor.md)|Inicializa la clase ActivationFactory.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
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