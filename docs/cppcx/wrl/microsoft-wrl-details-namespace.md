---
title: Microsoft::WRL::Details (Espacio de nombres)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: 4e8d2e5a2c7e6655674c4e965cd7222d930dff9a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213790"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details (Espacio de nombres)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>Members

### <a name="classes"></a>Clases

|Nombre|Descripción|
|----------|-----------------|
|[ComPtrRef (clase)](comptrref-class.md)|Representa una referencia a un objeto de tipo ComPtr\<T >.|
|[ComPtrRefBase (clase)](comptrrefbase-class.md)|Representa la clase base para la clase [ComPtrRef](comptrref-class.md) .|
|[DontUseNewUseMake (clase)](dontusenewusemake-class.md)|Evita el uso de operadores `new` en `RuntimeClass`. Por lo tanto, debe usar la [función make](make-function.md) en su lugar.|
|[EventTargetArray (clase)](eventtargetarray-class.md)|Representa una matriz de controladores de eventos.|
|[MakeAllocator (clase)](makeallocator-class.md)|Asigna memoria para una clase activable, con o sin compatibilidad de referencia débil.|
|[ModuleBase (clase)](modulebase-class.md)|Representa la clase base de las clases de [módulo](module-class.md) .|
|[RemoveIUnknown (clase)](removeiunknown-class.md)|Crea un tipo que es equivalente a un tipo basado en `IUnknown`, pero tiene métodos `QueryInterface`, `AddRef`y `Release` no virtuales.|
|[WeakReference (clase)](weakreference-class.md)|Representa una *referencia débil* que se puede usar con el Windows Runtime o com clásico. Una referencia débil representa un objeto que puede ser o no accesible.|

### <a name="structures"></a>Estructuras

|Nombre|Descripción|
|----------|-----------------|
|[ArgTraits (estructura)](argtraits-structure.md)|Declara una interfaz de delegado especificada y una función miembro anónima que tiene un número especificado de parámetros.|
|[ArgTraitsHelper (estructura)](argtraitshelper-structure.md)|Ayuda a definir características comunes de los argumentos de delegado.|
|[BoolStruct (estructura)](boolstruct-structure.md)|Define si un `ComPtr` está administrando la duración del objeto de una interfaz. el operador [booltype (()](comptr-class.md#operator-microsoft-wrl-details-booltype) utiliza internamente `BoolStruct`.|
|[CreatorMap (estructura)](creatormap-structure.md)|Contiene información sobre cómo inicializar, registrar y anular el registro de objetos.|
|[DerefHelper (estructura)](derefhelper-structure.md)|Representa un puntero desreferenciado al parámetro de plantilla `T*`.|
|[EnableIf (estructura)](enableif-structure.md)|Define un miembro de datos del tipo especificado por el segundo parámetro de plantilla si el primer parámetro de plantilla se evalúa como `true`.|
|[FactoryCache (estructura)](factorycache-structure.md)|Contiene la ubicación de un generador de clases y un valor que identifica un Windows Runtime registrado o un objeto de clase COM.|
|[ImplementsBase (estructura)](implementsbase-structure.md)|Se usa para validar los tipos de parámetro de plantilla en la [estructura de implementaciones](implements-structure.md).|
|[ImplementsHelper (estructura)](implementshelper-structure.md)|Ayuda a implementar la estructura [Implements](implements-structure.md) .|
|[InterfaceList (estructura)](interfacelist-structure.md)|Se utiliza para crear una lista recursiva de interfaces.|
|[InterfaceListHelper (estructura)](interfacelisthelper-structure.md)|Compila un tipo de `InterfaceList` mediante la aplicación de los argumentos de parámetro de plantilla especificados de forma recursiva.|
|[InterfaceTraits (estructura)](interfacetraits-structure.md)|Implementa características comunes de una interfaz.|
|[InvokeHelper (estructura)](invokehelper-structure.md)|Proporciona una implementación del método `Invoke()` basándose en el número y tipo de argumentos especificados.|
|[IsBaseOfStrict (estructura)](isbaseofstrict-structure.md)|Comprueba si un tipo es la base de otro.|
|[IsSame (estructura)](issame-structure.md)|Comprueba si un tipo especificado es igual que otro tipo especificado.|
|[Nil (estructura)](nil-structure.md)|Se usa para indicar un parámetro de plantilla opcional no especificado.|
|[RemoveReference (estructura)](removereference-structure.md)|Quita la referencia o el rasgo de referencia rvalue del parámetro de plantilla de clase especificado.|
|[RuntimeClassBase (estructura)](runtimeclassbase-structure.md)|Se utiliza para detectar `RuntimeClass` en la función [Make](make-function.md) .|
|[RuntimeClassBaseT (estructura)](runtimeclassbaset-structure.md)|Proporciona métodos auxiliares para operaciones de `QueryInterface` y obtener los identificadores de interfaz.|
|[VerifyInheritanceHelper (estructura)](verifyinheritancehelper-structure.md)|Comprueba si una interfaz se deriva de otra interfaz.|
|[VerifyInterfaceHelper (estructura)](verifyinterfacehelper-structure.md)|Comprueba que la interfaz especificada por el parámetro de plantilla cumple determinados requisitos.|

### <a name="enumerations"></a>Enumeraciones

|Nombre|Descripción|
|----------|-----------------|
|[AsyncStatusInternal (enumeración)](asyncstatusinternal-enumeration.md)|Especifica una asignación entre las enumeraciones internas para el estado de las operaciones asincrónicas y la enumeración `Windows::Foundation::AsyncStatus`.|

### <a name="functions"></a>Functions

|Nombre|Descripción|
|----------|-----------------|
|[ActivationFactoryCallback (función)](activationfactorycallback-function.md)|Obtiene el generador de activación para el identificador de activación especificado.|
|[Move (función)](move-function.md)|Mueve el argumento especificado de una ubicación a otra.|
|[RaiseException (función)](raiseexception-function.md)|Genera una excepción en el subproceso que realiza la llamada.|
|[Swap (función) (WRL)](swap-function-wrl.md)|Intercambia los valores de los dos argumentos especificados.|
|[TerminateMap (función)](terminatemap-function.md)|Cierra los generadores de clase en el módulo especificado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** Async. h, Client. h, corewrappers. h, Event. h, FTM. h, implementa. h, Internal. h, Module. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers (espacio de nombres)](microsoft-wrl-wrappers-namespace.md)
