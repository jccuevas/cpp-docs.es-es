---
title: Microsoft::WRL (Espacio de nombres)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL
- module/Microsoft::WRL
- async/Microsoft::WRL
- internal/Microsoft::WRL
- event/Microsoft::WRL
- ftm/Microsoft::WRL
- client/Microsoft::WRL
- corewrappers/Microsoft::WRL
helpviewer_keywords:
- WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
ms.openlocfilehash: d402f2a1292088b52ce921bbc0007ab96554189e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785779"
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL (Espacio de nombres)

Define los tipos fundamentales que componen la biblioteca de plantillas C++ de Windows en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
namespace Microsoft::WRL;
```

## <a name="members"></a>Miembros

### <a name="typedefs"></a>Typedefs

|Name|Descripción|
|----------|-----------------|
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt | InhibitWeakReference>`|

### <a name="classes"></a>Clases

|Name|Descripción|
|----------|-----------------|
|[ActivationFactory (clase)](activationfactory-class.md)|Habilita una o más clases que activa Windows en tiempo de ejecución.|
|[AsyncBase (clase)](asyncbase-class.md)|Implementa la máquina de estados asincrónica de Windows Runtime.|
|[ClassFactory (clase)](classfactory-class.md)|Implementa la funcionalidad básica de la interfaz `IClassFactory`.|
|[ComPtr (clase)](comptr-class.md)|Crea un tipo de *puntero inteligente* que representa la interfaz especificada por el parámetro de plantilla. ComPtr mantiene automáticamente un recuento de referencias para el puntero de la interfaz subyacente y la libera cuando el recuento de referencias llega a cero.|
|[DeferrableEventArgs (clase)](deferrableeventargs-class.md)|Clase de plantilla usada para los tipos de argumento de evento de los aplazamientos.|
|[EventSource (clase)](eventsource-class.md)|Representa un evento. Las funciones miembro `EventSource` agregan, quitan e invocan controladores de eventos.|
|[FtmBase (clase)](ftmbase-class.md)|Representa un objeto de cálculo de referencias con subprocesamiento libre.|
|[Module (clase)](module-class.md)|Representa una colección de objetos relacionados.|
|[RuntimeClass (clase)](runtimeclass-class.md)|Representa una clase con instancias que hereda el número especificado de interfaces y proporciona la compatibilidad especificada con Windows Runtime, COM clásico y referencia débil.|
|[SimpleActivationFactory (clase)](simpleactivationfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base de Windows en tiempo de ejecución o COM clásico.|
|[SimpleClassFactory (clase)](simpleclassfactory-class.md)|Proporciona un mecanismo fundamental para crear una clase base.|
|[WeakRef (clase)](weakref-class.md)|Representa una *referencia débil* que solo puede usar Windows en tiempo de ejecución, no COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.|

### <a name="structures"></a>Estructuras

|Name|Descripción|
|----------|-----------------|
|[ChainInterfaces (estructura)](chaininterfaces-structure.md)|Especifica las funciones de comprobación e inicialización que se pueden aplicar a un conjunto de identificadores de interfaz.|
|[CloakedIid (estructura)](cloakediid-structure.md)|Indica a la `RuntimeClass`, `Implements` y `ChainInterfaces` plantillas que la interfaz especificada no es accesible en la lista IID.|
|[Implements (estructura)](implements-structure.md)|Implementa `QueryInterface` y `GetIid` para las interfaces especificadas.|
|[MixIn (estructura)](mixin-structure.md)|Garantiza que una clase en tiempo de ejecución deriva de interfaces de Windows en tiempo de ejecución, si las hubiera, y luego de interfaces de COM clásico.|
|[RuntimeClassFlags (estructura)](runtimeclassflags-structure.md)|Contiene el tipo de una instancia de un [RuntimeClass](runtimeclass-class.md).|

### <a name="enumerations"></a>Enumeraciones

|Name|Descripción|
|----------|-----------------|
|[AsyncResultType (enumeración)](asyncresulttype-enumeration.md)|Especifica el tipo de resultado devuelto por la `GetResults()` método.|
|[ModuleType (enumeración)](moduletype-enumeration.md)|Especifica si un módulo debe admitir un servidor en proceso o un servidor fuera de proceso.|
|[RuntimeClassType (enumeración)](runtimeclasstype-enumeration.md)|Especifica el tipo de [RuntimeClass](runtimeclass-class.md) instancia que se admite.|

### <a name="functions"></a>Funciones

|Name|Descripción|
|----------|-----------------|
|[AsWeak (función)](asweak-function.md)|Recupera una referencia débil a una instancia especificada.|
|[Callback (función) (WRL)](callback-function-wrl.md)|Crea un objeto cuya función de miembro es un método de devolución de llamada.|
|[CreateActivationFactory (función)](createactivationfactory-function.md)|Crea un generador que produce instancias de la clase especificada que puede activar Windows en tiempo de ejecución.|
|[CreateClassFactory (función)](createclassfactory-function.md)|Crea un generador que produce instancias de la clase especificada.|
|[Make (función)](make-function.md)|Inicializa la clase en tiempo de ejecución de Windows especificada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers (espacio de nombres)](microsoft-wrl-wrappers-namespace.md)