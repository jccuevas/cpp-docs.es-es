---
title: FtmBase (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
dev_langs:
- C++
helpviewer_keywords:
- FtmBase class
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 662e40dd7e111b976be105129861b8ea26e5d0d9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646181"
---
# <a name="ftmbase-class"></a>FtmBase (clase)
Representa un objeto de cálculo de referencias con subprocesamiento libre.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
class FtmBase : public Microsoft::WRL::Implements<  
   Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,   
   Microsoft::WRL::CloakedIid<IMarshal> >;  
```  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [RuntimeClass (clase)](runtimeclass-class.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[FtmBase::FtmBase (constructor)](../windows/ftmbase-ftmbase-constructor.md)|Inicializa una nueva instancia de la **FtmBase** clase.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[FtmBase::CreateGlobalInterfaceTable (método)](../windows/ftmbase-createglobalinterfacetable-method.md)|Crea una tabla de interfaz global (GIT).|  
|[FtmBase::DisconnectObject (método)](../windows/ftmbase-disconnectobject-method.md)|Forzosamente libera todas las conexiones externas a un objeto. Servidor del objeto llama a la implementación del objeto de este método antes de apagar.|  
|[FtmBase::GetMarshalSizeMax (método)](../windows/ftmbase-getmarshalsizemax-method.md)|Obtenga el límite superior en el número de bytes necesarios para serializar el puntero de interfaz especificado en el objeto especificado.|  
|[FtmBase::GetUnmarshalClass (método)](../windows/ftmbase-getunmarshalclass-method.md)|Obtiene el CLSID que COM que se utiliza para localizar el archivo DLL que contiene el código para el proxy correspondiente. COM carga este archivo DLL para crear una instancia del proxy no inicializada.|  
|[FtmBase::MarshalInterface (método)](../windows/ftmbase-marshalinterface-method.md)|Escribe los datos necesarios para inicializar un objeto de proxy en algún proceso de cliente en una secuencia.|  
|[FtmBase::ReleaseMarshalData (método)](../windows/ftmbase-releasemarshaldata-method.md)|Destruye un paquete de cálculo de referencias de datos.|  
|[FtmBase::UnmarshalInterface (método)](../windows/ftmbase-unmarshalinterface-method.md)|Inicializa a un proxy recién creado y devuelve un puntero de interfaz a ese proxy.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[FtmBase::marshaller_ (miembro de datos)](../windows/ftmbase-marshaller-data-member.md)|Contiene una referencia para el contador de referencias de subproceso libre.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `FtmBase`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ftm.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)