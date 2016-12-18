---
title: "Microsoft::WRL (Espacio de nombres) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL"
  - "module/Microsoft::WRL"
  - "async/Microsoft::WRL"
  - "internal/Microsoft::WRL"
  - "event/Microsoft::WRL"
  - "ftm/Microsoft::WRL"
  - "client/Microsoft::WRL"
  - "corewrappers/Microsoft::WRL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "espacio de nombres de WRL"
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Microsoft::WRL (Espacio de nombres)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define los tipos fundamentales que componen el [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace Microsoft::WRL;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="typedefs"></a>Typedefs  
  
|Name|Descripción|  
|----------|-----------------|  
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt &#124; InhibitWeakReference>`|  
  
### <a name="classes"></a>Clases  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[ActivationFactory (clase)](../windows/activationfactory-class.md)|Habilita una o más clases que activa Windows Runtime.|  
|[AsyncBase (clase)](../windows/asyncbase-class.md)|Implementa la máquina de estados asincrónica de Windows Runtime.|  
|[ClassFactory (clase)](../windows/classfactory-class.md)|Implementa la funcionalidad básica de la interfaz `IClassFactory`.|  
|[ComPtr (clase)](../windows/comptr-class.md)|Crea un tipo de *puntero inteligente* que representa la interfaz especificada por el parámetro de plantilla. ComPtr mantiene automáticamente un recuento de referencias para el puntero de la interfaz subyacente y la libera cuando el recuento de referencias llega a cero.|  
|[Clase DeferrableEventArgs](../windows/deferrableeventargs-class.md)|Una clase de plantilla utilizada para los tipos de argumento de evento de los aplazamientos.|  
|[EventSource (clase)](../windows/eventsource-class.md)|Representa un evento. Las funciones miembro `EventSource` agregan, quitan e invocan controladores de eventos.|  
|[FtmBase (clase)](../windows/ftmbase-class.md)|Representa un objeto de cálculo de referencias con subprocesamiento libre.|  
|[Module (clase)](../windows/module-class.md)|Representa una colección de objetos relacionados.|  
|[RuntimeClass (clase)](../windows/runtimeclass-class.md)|Representa una clase con instancias que hereda el número especificado de interfaces y proporciona la compatibilidad especificada con Windows Runtime, COM clásico y referencia débil.|  
|[SimpleActivationFactory (clase)](../windows/simpleactivationfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base de Windows Runtime o COM clásico.|  
|[SimpleClassFactory (clase)](../windows/simpleclassfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base.|  
|[WeakRef (clase)](../windows/weakref-class.md)|Representa un *referencia débil* que se puede utilizar sólo el Runtime de Windows, COM clásico no. Una referencia débil representa un objeto que puede ser o no accesible.|  
  
### <a name="structures"></a>Estructuras  
  
|Name|Descripción|  
|----------|-----------------|  
|[ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)|Especifica las funciones de comprobación e inicialización que se pueden aplicar a un conjunto de identificadores de interfaz.|  
|[CloakedIid (estructura)](../windows/cloakediid-structure.md)|Indica a las plantillas RuntimeClass, Implements y ChainInterfaces que la interfaz especificada no es accesible en la lista IID.|  
|[Implements (estructura)](../Topic/Implements%20Structure.md)|Implementa QueryInterface y GetIid para las interfaces especificadas.|  
|[MixIn (estructura)](../windows/mixin-structure.md)|Garantiza que una clase Runtime deriva de interfaces de Windows Runtime, si las hubiera, y luego de interfaces de COM clásico.|  
|[RuntimeClassFlags (estructura)](../windows/runtimeclassflags-structure.md)|Contiene el tipo de una instancia de un [RuntimeClass](../windows/runtimeclass-class.md).|  
  
### <a name="enumerations"></a>Enumeraciones  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[AsyncResultType (enumeración)](../windows/asyncresulttype-enumeration.md)|Especifica el tipo de resultado devuelto por el método GetResults().|  
|[ModuleType (enumeración)](../Topic/ModuleType%20Enumeration.md)|Especifica si un módulo debe admitir un servidor en proceso o un servidor fuera de proceso.|  
|[RuntimeClassType (enumeración)](../windows/runtimeclasstype-enumeration.md)|Especifica el tipo de [RuntimeClass](../windows/runtimeclass-class.md) instancia que se admite.|  
  
### <a name="functions"></a>Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[AsWeak (función)](../windows/asweak-function.md)|Recupera una referencia débil a una instancia especificada.|  
|[Función de devolución de llamada](../windows/callback-function-windows-runtime-cpp-template-library.md)|Crea un objeto cuya función de miembro es un método de devolución de llamada.|  
|[CreateActivationFactory (función)](../windows/createactivationfactory-function.md)|Crea un generador que produce instancias de la clase especificada que puede activar Windows Runtime.|  
|[CreateClassFactory (función)](../windows/createclassfactory-function.md)|Crea un generador que produce instancias de la clase especificada.|  
|[MAKE (función)](../windows/make-function.md)|Inicializa la clase [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres Wrappers](../Topic/Microsoft::WRL::Wrappers%20Namespace.md)