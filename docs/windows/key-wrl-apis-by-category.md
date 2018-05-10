---
title: La clave de API WRL por categoría | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9936c85443f893111b3c2b9de17ca80e6fb382b2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="key-wrl-apis-by-category"></a>API clave de WRL por categoría
Las tablas siguientes enumeran principal clases, structs, funciones y macros de biblioteca de plantillas de C++ de Windows en tiempo de ejecución. Se omiten las construcciones en clases y espacios de nombres de aplicación auxiliar. Estas listas aumentan la documentación de API, que está organizada por espacio de nombres.  
  
### <a name="classes"></a>Clases  
  
|Title|Descripción|  
|-----------|-----------------|  
|[ActivationFactory (clase)](../windows/activationfactory-class.md)|Habilita una o más clases que activa Windows Runtime.|  
|[AsyncBase (clase)](../windows/asyncbase-class.md)|Implementa la máquina de estados asincrónica de Windows Runtime.|  
|[ClassFactory (clase)](../windows/classfactory-class.md)|Implementa la funcionalidad básica de la interfaz `IClassFactory`.|  
|[ComPtr (clase)](../windows/comptr-class.md)|Crea un tipo de *puntero inteligente* que representa la interfaz especificada por el parámetro de plantilla. ComPtr mantiene automáticamente un recuento de referencias para el puntero de la interfaz subyacente y la libera cuando el recuento de referencias llega a cero.|  
|[Event (clase) (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)](../windows/event-class-windows-runtime-cpp-template-library.md)|Representa un evento.|  
|[EventSource (clase)](../windows/eventsource-class.md)|Representa un evento. Las funciones miembro `EventSource` agregan, quitan e invocan controladores de eventos.|  
|[FtmBase (clase)](../windows/ftmbase-class.md)|Representa un objeto de cálculo de referencias con subprocesamiento libre.|  
|[HandleT (clase)](../windows/handlet-class.md)|Representa un identificador a un objeto.|  
|[HString (clase)](../windows/hstring-class.md)|Proporciona compatibilidad para la manipulación de identificadores HSTRING.|  
|[HStringReference (clase)](../windows/hstringreference-class.md)|Representa un HSTRING que se crea a partir de una cadena existente.|  
|[Module (clase)](../windows/module-class.md)|Representa una colección de objetos relacionados.|  
|[Module::GenericReleaseNotifier (clase)](../windows/module-genericreleasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto en el módulo actual. El controlador de eventos se especifica por en una expresión lambda, functor o puntero a función.|  
|[Module::MethodReleaseNotifier (clase)](../windows/module-methodreleasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto en el módulo actual. El controlador de eventos se especifica mediante un objeto y su miembro de puntero a un método.|  
|[Module::ReleaseNotifier (clase)](../windows/module-releasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto en un módulo.|  
|[RoInitializeWrapper (clase)](../windows/roinitializewrapper-class.md)|Inicializa el tiempo de ejecución de Windows.|  
|[RuntimeClass (clase)](../windows/runtimeclass-class.md)|Representa una clase con instancias que hereda el número especificado de interfaces y proporciona la compatibilidad especificada con Windows Runtime, COM clásico y referencia débil.|  
|[SimpleActivationFactory (clase)](../windows/simpleactivationfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base de Windows Runtime o COM clásico.|  
|[SimpleClassFactory (clase)](../windows/simpleclassfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base.|  
|[WeakRef (clase)](../windows/weakref-class.md)|Representa una *referencia débil* que solo puede usar Windows en tiempo de ejecución, no COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.|  
  
### <a name="structures"></a>Estructuras  
  
|Title|Descripción|  
|-----------|-----------------|  
|[ChainInterfaces (estructura)](../windows/chaininterfaces-structure.md)|Especifica las funciones de comprobación e inicialización que se pueden aplicar a un conjunto de identificadores de interfaz.|  
|[CloakedIid (estructura)](../windows/cloakediid-structure.md)|Indica a la `RuntimeClass`, `Implements` y `ChainInterfaces` plantillas que la interfaz especificada no es accesible en la lista IID.|  
|[Implements (estructura)](../windows/implements-structure.md)|Implementa `QueryInterface` y `GetIid` para las interfaces especificadas.|  
|[MixIn (estructura)](../windows/mixin-structure.md)|Garantiza que una clase Runtime deriva de interfaces de Windows Runtime, si las hubiera, y luego de interfaces de COM clásico.|  
  
### <a name="functions"></a>Funciones  
  
|Title|Descripción|  
|-----------|-----------------|  
|[ActivateInstance (función)](../windows/activateinstance-function.md)|Registra y recupera una instancia de un tipo especificado definido en un identificador de clase especificada.|  
|[AsWeak (función)](../windows/asweak-function.md)|Recupera una referencia débil a una instancia especificada.|  
|[Función de devolución de llamada](../windows/callback-function-windows-runtime-cpp-template-library.md)|Crea un objeto cuya función de miembro es un método de devolución de llamada.|  
|[CreateActivationFactory (función)](../windows/createactivationfactory-function.md)|Crea un generador que produce instancias de la clase especificada que puede activar Windows Runtime.|  
|[CreateClassFactory (función)](../windows/createclassfactory-function.md)|Crea un generador que produce instancias de la clase especificada.|  
|[GetActivationFactory (función)](../windows/getactivationfactory-function.md)|Recupera un generador de activación para el tipo especificado por el parámetro de plantilla.|  
|[Make (función)](../windows/make-function.md)|Inicializa la clase en tiempo de ejecución de Windows especificada.|  
  
### <a name="macros"></a>Macros  
  
|Title|Descripción|  
|-----------|-----------------|  
|[ActivatableClass (macros)](../windows/activatableclass-macros.md)|Rellena una caché interna que contiene una fábrica que puede crear una instancia de la clase especificada.|  
|[InspectableClass (macro)](../windows/inspectableclass-macro.md)|Establece el nivel de confianza y de nombre de clase en tiempo de ejecución.|  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)