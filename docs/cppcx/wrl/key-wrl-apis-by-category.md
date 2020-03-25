---
title: API clave de WRL por categoría
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
ms.openlocfilehash: 8ac89f3286866ac61bac5ae256bdb448fe88f07d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213829"
---
# <a name="key-wrl-apis-by-category"></a>API clave de WRL por categoría

En las tablas siguientes se enumeran las clases, las estructuras, las funciones y las macros principales Windows Runtime C++ biblioteca de plantillas. Se omiten las construcciones de los espacios de nombres y las clases auxiliares. Estas listas amplían la documentación de la API, que está organizada por espacio de nombres.

## <a name="classes"></a>Clases

|Título|Descripción|
|-----------|-----------------|
|[ActivationFactory (clase)](activationfactory-class.md)|Habilita una o más clases que activa Windows en tiempo de ejecución.|
|[AsyncBase (clase)](asyncbase-class.md)|Implementa la máquina de estados asincrónica de Windows Runtime.|
|[ClassFactory (clase)](classfactory-class.md)|Implementa la funcionalidad básica de la interfaz `IClassFactory`.|
|[ComPtr (clase)](comptr-class.md)|Crea un tipo de *puntero inteligente* que representa la interfaz especificada por el parámetro de plantilla. ComPtr mantiene automáticamente un recuento de referencias para el puntero de la interfaz subyacente y la libera cuando el recuento de referencias llega a cero.|
|[Event (clase) (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)](event-class-wrl.md)|Representa un evento.|
|[clase EventSource](eventsource-class.md)|Representa un evento. Las funciones miembro `EventSource` agregan, quitan e invocan controladores de eventos.|
|[FtmBase (clase)](ftmbase-class.md)|Representa un objeto de cálculo de referencias con subprocesamiento libre.|
|[HandleT (clase)](handlet-class.md)|Representa un identificador de un objeto.|
|[HString (clase)](hstring-class.md)|Proporciona compatibilidad para manipular los identificadores de HSTRING.|
|[HStringReference (clase)](hstringreference-class.md)|Representa un HSTRING que se crea a partir de una cadena existente.|
|[Module (clase)](module-class.md)|Representa una colección de objetos relacionados.|
|[Module::GenericReleaseNotifier (clase)](module-genericreleasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica mediante en una expresión lambda, functor o de puntero a función.|
|[Module::MethodReleaseNotifier (clase)](module-methodreleasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica mediante un objeto y su miembro de puntero a método.|
|[Module::ReleaseNotifier (clase)](module-releasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto de un módulo.|
|[RoInitializeWrapper (clase)](roinitializewrapper-class.md)|Inicializa el Windows Runtime.|
|[RuntimeClass (clase)](runtimeclass-class.md)|Representa una clase con instancias que hereda el número especificado de interfaces y proporciona la compatibilidad especificada con Windows Runtime, COM clásico y referencia débil.|
|[SimpleActivationFactory (clase)](simpleactivationfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base de Windows en tiempo de ejecución o COM clásico.|
|[SimpleClassFactory (clase)](simpleclassfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base.|
|[WeakRef (clase)](weakref-class.md)|Representa una *referencia débil* que solo puede usar Windows en tiempo de ejecución, no COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.|

## <a name="structures"></a>Estructuras

|Título|Descripción|
|-----------|-----------------|
|[ChainInterfaces (estructura)](chaininterfaces-structure.md)|Especifica las funciones de comprobación e inicialización que se pueden aplicar a un conjunto de identificadores de interfaz.|
|[CloakedIid (estructura)](cloakediid-structure.md)|Indica al `RuntimeClass`, `Implements` y `ChainInterfaces` plantillas a las que no se puede tener acceso a la interfaz especificada en la lista de IID.|
|[Implements (estructura)](implements-structure.md)|Implementa `QueryInterface` y `GetIid` para las interfaces especificadas.|
|[MixIn (estructura)](mixin-structure.md)|Garantiza que una clase en tiempo de ejecución deriva de interfaces de Windows en tiempo de ejecución, si las hubiera, y luego de interfaces de COM clásico.|

## <a name="functions"></a>Functions

|Título|Descripción|
|-----------|-----------------|
|[ActivateInstance (función)](activateinstance-function.md)|Registra y recupera una instancia de un tipo especificado definido en un identificador de clase especificado.|
|[AsWeak (función)](asweak-function.md)|Recupera una referencia débil a una instancia especificada.|
|[Función de devolución de llamada](callback-function-wrl.md)|Crea un objeto cuya función de miembro es un método de devolución de llamada.|
|[CreateActivationFactory (función)](createactivationfactory-function.md)|Crea un generador que produce instancias de la clase especificada que puede activar Windows en tiempo de ejecución.|
|[CreateClassFactory (función)](createclassfactory-function.md)|Crea un generador que produce instancias de la clase especificada.|
|[GetActivationFactory (función)](getactivationfactory-function.md)|Recupera un generador de activación para el tipo especificado por el parámetro de plantilla.|
|[Make (función)](make-function.md)|Inicializa la clase de Windows Runtime especificada.|

## <a name="macros"></a>Macros

|Título|Descripción|
|-----------|-----------------|
|[ActivatableClass (macros)](activatableclass-macros.md)|Rellena una memoria caché interna que contiene un generador que puede crear una instancia de la clase especificada.|
|[InspectableClass (macro)](inspectableclass-macro.md)|Establece el nombre de clase en tiempo de ejecución y el nivel de confianza.|

## <a name="see-also"></a>Consulte también

[Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](windows-runtime-cpp-template-library-wrl.md)
