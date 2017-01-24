---
title: "API clave de WRL por categor&#237;a | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# API clave de WRL por categor&#237;a
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las tablas siguientes enumeran principal [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] clases, structs, funciones y macros. Se omiten las construcciones en clases y espacios de nombres de aplicación auxiliar. Estas listas aumentan la documentación de API, que está organizada por espacio de nombres.  
  
### <a name="classes"></a>Clases  
  
|Título|Descripción|  
|-----------|-----------------|  
|[ActivationFactory (clase)](../windows/activationfactory-class.md)|Habilita una o más clases que activa Windows Runtime.|  
|[AsyncBase (clase)](../windows/asyncbase-class.md)|Implementa la máquina de estados asincrónica de Windows Runtime.|  
|[ClassFactory (clase)](../windows/classfactory-class.md)|Implementa la funcionalidad básica de la interfaz `IClassFactory`.|  
|[ComPtr (clase)](../windows/comptr-class.md)|Crea un tipo de *puntero inteligente* que representa la interfaz especificada por el parámetro de plantilla. ComPtr mantiene automáticamente un recuento de referencias para el puntero de la interfaz subyacente y la libera cuando el recuento de referencias llega a cero.|  
|[Clase de eventos (biblioteca de plantillas de C++ en tiempo de ejecución de Windows)](../windows/event-class-windows-runtime-cpp-template-library.md)|Representa un evento.|  
|[EventSource (clase)](../windows/eventsource-class.md)|Representa un evento. Las funciones miembro `EventSource` agregan, quitan e invocan controladores de eventos.|  
|[FtmBase (clase)](../windows/ftmbase-class.md)|Representa un objeto de cálculo de referencias con subprocesamiento libre.|  
|[HandleT (clase)](../Topic/HandleT%20Class.md)|Representa un identificador a un objeto.|  
|[HString (clase)](../windows/hstring-class.md)|Proporciona compatibilidad para manipular los identificadores HSTRING.|  
|[HStringReference (clase)](../windows/hstringreference-class.md)|Representa una cadena HSTRING creada a partir de una cadena existente.|  
|[Module (clase)](../windows/module-class.md)|Representa una colección de objetos relacionados.|  
|[Genericreleasenotifier (clase)](../windows/module-genericreleasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica en una expresión lambda, un functor o un puntero a función.|  
|[Methodreleasenotifier (clase)](../Topic/Module::MethodReleaseNotifier%20Class.md)|Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos especificado por un objeto y su miembro de puntero a método.|  
|[Releasenotifier (clase)](../Topic/Module::ReleaseNotifier%20Class.md)|Invoca un controlador de eventos cuando se libera el último objeto de un módulo.|  
|[RoInitializeWrapper (clase)](RoInitializeWrapper%20Class.md)|Inicializa el [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].|  
|[RuntimeClass (clase)](../windows/runtimeclass-class.md)|Representa una clase con instancias que hereda el número especificado de interfaces y proporciona la compatibilidad especificada con Windows Runtime, COM clásico y referencia débil.|  
|[SimpleActivationFactory (clase)](../windows/simpleactivationfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base de Windows Runtime o COM clásico.|  
|[SimpleClassFactory (clase)](../windows/simpleclassfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base.|  
|[WeakRef (clase)](../windows/weakref-class.md)|Representa un *referencia débil* que se puede utilizar sólo el Runtime de Windows, COM clásico no. Una referencia débil representa un objeto que puede ser o no accesible.|  
  
### <a name="structures"></a>Estructuras  
  
|Título|Descripción|  
|-----------|-----------------|  
|[ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)|Especifica las funciones de comprobación e inicialización que se pueden aplicar a un conjunto de identificadores de interfaz.|  
|[CloakedIid (estructura)](../windows/cloakediid-structure.md)|Indica a la `RuntimeClass`, `Implements` y `ChainInterfaces` que la interfaz especificada no es accesible en la lista IID de plantillas.|  
|[Implements (estructura)](../Topic/Implements%20Structure.md)|Implementa `QueryInterface` y `GetIid` para las interfaces especificadas.|  
|[MixIn (estructura)](../windows/mixin-structure.md)|Garantiza que una clase Runtime deriva de interfaces de Windows Runtime, si las hubiera, y luego de interfaces de COM clásico.|  
  
### <a name="functions"></a>Funciones  
  
|Título|Descripción|  
|-----------|-----------------|  
|[ActivateInstance (función)](../windows/activateinstance-function.md)|Registra y recupera una instancia de un tipo especificado definido en un identificador de clase especificado.|  
|[AsWeak (función)](../windows/asweak-function.md)|Recupera una referencia débil a una instancia especificada.|  
|[Función de devolución de llamada](../windows/callback-function-windows-runtime-cpp-template-library.md)|Crea un objeto cuya función de miembro es un método de devolución de llamada.|  
|[CreateActivationFactory (función)](../windows/createactivationfactory-function.md)|Crea un generador que produce instancias de la clase especificada que puede activar Windows Runtime.|  
|[CreateClassFactory (función)](../windows/createclassfactory-function.md)|Crea un generador que produce instancias de la clase especificada.|  
|[GetActivationFactory (función)](../windows/getactivationfactory-function.md)|Recupera un generador de activación para el tipo especificado por el parámetro de plantilla.|  
|[MAKE (función)](../windows/make-function.md)|Inicializa la clase [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] especificada.|  
  
### <a name="macros"></a>Macros  
  
|Título|Descripción|  
|-----------|-----------------|  
|[ActivatableClass (Macros)](../Topic/ActivatableClass%20Macros.md)|Rellena una caché interna que contiene una fábrica que puede crear una instancia de la clase especificada.|  
|[InspectableClass (macro)](../windows/inspectableclass-macro.md)|Establece el nivel de confianza y de nombre de clase en tiempo de ejecución.|  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../Topic/Windows%20Runtime%20C++%20Template%20Library%20\(WRL\).md)