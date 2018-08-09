---
title: ClassFactory (clase) | Microsoft Docs
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
ms.openlocfilehash: c9a7caba7ccfb8f5764a1f460835ff540c838975
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641046"
---
# <a name="classfactory-class"></a>ClassFactory (clase)
Implementa la funcionalidad básica de la interfaz `IClassFactory`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
  
### <a name="parameters"></a>Parámetros  
 *I0*  
 La interfaz de cero.  
  
 *I1*  
 La primera interfaz.  
  
 *I2*  
 La segunda interfaz.  
  
## <a name="remarks"></a>Comentarios  
 Usar **ClassFactory** para proporcionar una implementación de fábrica definido por el usuario.  
  
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
|[ClassFactory::AddRef (método)](../windows/classfactory-addref-method.md)|Incrementa el recuento de referencias actual **ClassFactory** objeto.|  
|[ClassFactory::LockServer (método)](../windows/classfactory-lockserver-method.md)|Incrementa o disminuye el número de subyacentes de objetos que se realiza el seguimiento actual **ClassFactory** objeto.|  
|[ClassFactory::QueryInterface (método)](../windows/classfactory-queryinterface-method.md)|Recupera un puntero a la interfaz especificada por el parámetro.|  
|[ClassFactory::Release (método)](../windows/classfactory-release-method.md)|Disminuye el recuento de referencias actual **ClassFactory** objeto.|  
  
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