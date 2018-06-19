---
title: ClassFactory (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
dev_langs:
- C++
helpviewer_keywords:
- ClassFactory class
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6294634652ffc6a53a577ccd75c348ed63c502e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858398"
---
# <a name="classfactory-class"></a>ClassFactory (clase)
Implementa la funcionalidad básica de la interfaz IClassFactory.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ClassFactory : public Details::RuntimeClass<  
   typename Details::InterfaceListHelper<IClassFactory,   
   I0,   
   I1,   
   I2,   
   Details::Nil>::TypeT,   
   RuntimeClassFlags<ClassicCom | InhibitWeakReference>,   
      false>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `I0`  
 La interfaz de cero.  
  
 `I1`  
 La primera interfaz.  
  
 `I2`  
 La segunda interfaz.  
  
## <a name="remarks"></a>Comentarios  
 Utilizar `ClassFactory` para proporcionar una implementación de generador definido por el usuario.  
  
 El modelo de programación siguiente muestra cómo utilizar el [implementa](../windows/implements-structure.md) estructura para especificar más de tres interfaces en un generador de clases.  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ClassFactory::ClassFactory (constructor)](../windows/classfactory-classfactory-constructor.md)||  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ClassFactory::AddRef (método)](../windows/classfactory-addref-method.md)|Incrementa el recuento de referencias para el objeto ClassFactory actual.|  
|[ClassFactory::LockServer (método)](../windows/classfactory-lockserver-method.md)|Incrementa o disminuye el número de subyacente de objetos que se realiza un seguimiento del objeto ClassFactory actual.|  
|[ClassFactory::QueryInterface (método)](../windows/classfactory-queryinterface-method.md)|Recupera un puntero a la interfaz especificada por el parámetro.|  
|[ClassFactory::Release (método)](../windows/classfactory-release-method.md)|Disminuye el recuento de referencias para el objeto ClassFactory actual.|  
  
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
  
 `ClassFactory`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft:: wrl Namespace](../windows/microsoft-wrl-namespace.md)   
 [RuntimeClassType (enumeración)](../windows/runtimeclasstype-enumeration.md)