---
title: API clave de WRL por categoría
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
ms.openlocfilehash: f3065323c567c944dab12fc1ebbcbd6bb57127e9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039063"
---
# <a name="key-wrl-apis-by-category"></a>API clave de WRL por categoría

Las tablas siguientes muestran las principales clases, structs, funciones y macros de biblioteca de plantillas C++ de Windows en tiempo de ejecución. Se omiten las construcciones en clases y espacios de nombres de aplicación auxiliar. Estas listas aumentan la documentación de API, que está organizada por espacio de nombres.

## <a name="classes"></a>Clases

|Título|Descripción|
|-----------|-----------------|
|[ActivationFactory (clase)](activationfactory-class.md)|Habilita una o más clases que activa Windows en tiempo de ejecución.|
|[AsyncBase (clase)](asyncbase-class.md)|Implementa la máquina de estados asincrónica de Windows Runtime.|
|[ClassFactory (clase)](classfactory-class.md)|Implementa la funcionalidad básica de la interfaz `IClassFactory`.|
|[ComPtr (clase)](comptr-class.md)|Crea un tipo de *puntero inteligente* que representa la interfaz especificada por el parámetro de plantilla. ComPtr mantiene automáticamente un recuento de referencias para el puntero de la interfaz subyacente y la libera cuando el recuento de referencias llega a cero.|
|[Event (clase) (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)](event-class-wrl.md)|Representa un evento.|
|[EventSource (clase)](eventsource-class.md)|Representa un evento. Las funciones miembro `EventSource` agregan, quitan e invocan controladores de eventos.|
|[FtmBase (clase)](ftmbase-class.md)|Representa un objeto de cálculo de referencias con subprocesamiento libre.|
|[HandleT (clase)](handlet-class.md)|Representa un identificador a un objeto.|
|[HString (clase)](hstring-class.md)|Proporciona compatibilidad para manipular los identificadores HSTRING.|
|[HStringReference (clase)](hstringreference-class.md)|Representa un objeto HSTRING que se crea a partir de una cadena existente.|
|[Module (clase)](module-class.md)|Representa una colección de objetos relacionados.|
|[Module::GenericReleaseNotifier (clase)](module-genericreleasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica por en una expresión lambda, functor o puntero a función.|
|[Module::MethodReleaseNotifier (clase)](module-methodreleasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto del módulo actual. El controlador de eventos se especifica mediante un objeto y su miembro de puntero al método.|
|[Module::ReleaseNotifier (clase)](module-releasenotifier-class.md)|Invoca un controlador de eventos cuando se libera el último objeto de un módulo.|
|[RoInitializeWrapper (clase)](roinitializewrapper-class.md)|Inicializa el tiempo de ejecución de Windows.|
|[RuntimeClass (clase)](runtimeclass-class.md)|Representa una clase con instancias que hereda el número especificado de interfaces y proporciona la compatibilidad especificada con Windows Runtime, COM clásico y referencia débil.|
|[SimpleActivationFactory (clase)](simpleactivationfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base de Windows en tiempo de ejecución o COM clásico.|
|[SimpleClassFactory (clase)](simpleclassfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base.|
|[WeakRef (clase)](weakref-class.md)|Representa una *referencia débil* que solo puede usar Windows en tiempo de ejecución, no COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.|

## <a name="structures"></a>Estructuras

|Título|Descripción|
|-----------|-----------------|
|[ChainInterfaces (estructura)](chaininterfaces-structure.md)|Especifica las funciones de comprobación e inicialización que se pueden aplicar a un conjunto de identificadores de interfaz.|
|[CloakedIid (estructura)](cloakediid-structure.md)|Indica a la `RuntimeClass`, `Implements` y `ChainInterfaces` plantillas que la interfaz especificada no es accesible en la lista IID.|
|[Implements (estructura)](implements-structure.md)|Implementa `QueryInterface` y `GetIid` para las interfaces especificadas.|
|[MixIn (estructura)](mixin-structure.md)|Garantiza que una clase en tiempo de ejecución deriva de interfaces de Windows en tiempo de ejecución, si las hubiera, y luego de interfaces de COM clásico.|

## <a name="functions"></a>Funciones

|Título|Descripción|
|-----------|-----------------|
|[ActivateInstance (función)](activateinstance-function.md)|Registra y recupera una instancia de un tipo especificado definido en un identificador de clase especificado.|
|[AsWeak (función)](asweak-function.md)|Recupera una referencia débil a una instancia especificada.|
|[Función de devolución de llamada](callback-function-wrl.md)|Crea un objeto cuya función de miembro es un método de devolución de llamada.|
|[CreateActivationFactory (función)](createactivationfactory-function.md)|Crea un generador que produce instancias de la clase especificada que puede activar Windows en tiempo de ejecución.|
|[CreateClassFactory (función)](createclassfactory-function.md)|Crea un generador que produce instancias de la clase especificada.|
|[GetActivationFactory (función)](getactivationfactory-function.md)|Recupera un generador de activación para el tipo especificado por el parámetro de plantilla.|
|[Make (función)](make-function.md)|Inicializa la clase en tiempo de ejecución de Windows especificada.|

## <a name="macros"></a>Macros

|Título|Descripción|
|-----------|-----------------|
|[ActivatableClass (macros)](activatableclass-macros.md)|Rellena una memoria caché interna que contiene una fábrica que puede crear una instancia de la clase especificada.|
|[InspectableClass (macro)](inspectableclass-macro.md)|Establece el nivel de confianza y de nombre de clase en tiempo de ejecución.|

## <a name="see-also"></a>Vea también

[Biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)](windows-runtime-cpp-template-library-wrl.md)