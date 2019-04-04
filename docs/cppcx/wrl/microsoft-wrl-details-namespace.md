---
title: Microsoft::WRL::Details (Espacio de nombres)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: 149b78a20061dc9083c62df4e58d638009c5e0a2
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785889"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details (Espacio de nombres)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>Miembros

### <a name="classes"></a>Clases

|Name|Descripción|
|----------|-----------------|
|[ComPtrRef (clase)](comptrref-class.md)|Representa una referencia a un objeto de tipo ComPtr\<T >.|
|[ComPtrRefBase (clase)](comptrrefbase-class.md)|Representa la clase base para el [ComPtrRef](comptrref-class.md) clase.|
|[DontUseNewUseMake (clase)](dontusenewusemake-class.md)|Impide el uso de operador `new` en `RuntimeClass`. Por lo tanto, debe usar el [función](make-function.md) en su lugar.|
|[EventTargetArray (clase)](eventtargetarray-class.md)|Representa una matriz de controladores de eventos.|
|[MakeAllocator (clase)](makeallocator-class.md)|Asigna memoria para una clase activable, con o sin compatibilidad con la referencia débil.|
|[ModuleBase (clase)](modulebase-class.md)|Representa la clase base de la [módulo](module-class.md) clases.|
|[RemoveIUnknown (clase)](removeiunknown-class.md)|Convierte un tipo que es equivalente a un `IUnknown`-tipo de función, pero tiene no virtual `QueryInterface`, `AddRef`, y `Release` métodos.|
|[WeakReference (clase)](weakreference-class.md)|Representa un *referencia débil* que puede utilizarse con el tiempo de ejecución de Windows o COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.|

### <a name="structures"></a>Estructuras

|Name|Descripción|
|----------|-----------------|
|[ArgTraits (estructura)](argtraits-structure.md)|Interfaz y una función miembro anónimo que tiene un número especificado de parámetros se declara a un delegado especificado.|
|[ArgTraitsHelper (estructura)](argtraitshelper-structure.md)|Ayuda a define las características comunes de los argumentos de delegado.|
|[BoolStruct (estructura)](boolstruct-structure.md)|Define si un `ComPtr` administra la duración del objeto de una interfaz. `BoolStruct` se usa internamente el [BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype) operador.|
|[CreatorMap (estructura)](creatormap-structure.md)|Contiene información acerca de cómo inicializar, registrar y anular el registro de objetos.|
|[DerefHelper (estructura)](derefhelper-structure.md)|Representa un puntero sin referencia a la `T*` parámetro de plantilla.|
|[EnableIf (estructura)](enableif-structure.md)|Define un miembro de datos del tipo especificado por el segundo parámetro de plantilla si se evalúa como el primer parámetro de plantilla `true`.|
|[FactoryCache (estructura)](factorycache-structure.md)|Contiene la ubicación de un generador de clases y un valor que identifica un objeto de clase en tiempo de ejecución de Windows o COM registrado.|
|[ImplementsBase (estructura)](implementsbase-structure.md)|Utilizado para validar los tipos de parámetro de plantilla en [Implements (estructura)](implements-structure.md).|
|[ImplementsHelper (estructura)](implementshelper-structure.md)|Ayuda a implementar la [implementa](implements-structure.md) estructura.|
|[InterfaceList (estructura)](interfacelist-structure.md)|Se utiliza para crear una lista recursiva de las interfaces.|
|[InterfaceListHelper (estructura)](interfacelisthelper-structure.md)|Compila una `InterfaceList` tipo mediante la aplicación de los argumentos de parámetro de plantilla especificado recursiva.|
|[InterfaceTraits (estructura)](interfacetraits-structure.md)|Características comunes de implementa de una interfaz.|
|[InvokeHelper (estructura)](invokehelper-structure.md)|Proporciona una implementación de la `Invoke()` método según el número especificado y el tipo de argumentos.|
|[IsBaseOfStrict (estructura)](isbaseofstrict-structure.md)|Comprueba si un tipo es la base de otro.|
|[IsSame (estructura)](issame-structure.md)|Las pruebas si un tipo especificado es igual que otro tipo especificado.|
|[Nil (estructura)](nil-structure.md)|Se utiliza para indicar un parámetro de plantilla opcional no especificado.|
|[RemoveReference (estructura)](removereference-structure.md)|Elimina el rasgo de referencia o referencia de rvalue desde el parámetro de plantilla de clase especificada.|
|[RuntimeClassBase (estructura)](runtimeclassbase-structure.md)|Utilizado para detectar `RuntimeClass` en el [realizar](make-function.md) función.|
|[RuntimeClassBaseT (estructura)](runtimeclassbaset-structure.md)|Proporciona métodos auxiliares para `QueryInterface` operaciones y obtener los identificadores de interfaz.|
|[VerifyInheritanceHelper (estructura)](verifyinheritancehelper-structure.md)|Comprueba si una interfaz se deriva de otra interfaz.|
|[VerifyInterfaceHelper (estructura)](verifyinterfacehelper-structure.md)|Comprueba que la interfaz especificada por el parámetro de plantilla cumple determinados requisitos.|

### <a name="enumerations"></a>Enumeraciones

|Name|Descripción|
|----------|-----------------|
|[AsyncStatusInternal (enumeración)](asyncstatusinternal-enumeration.md)|Especifica una asignación entre enumeraciones internas para el estado de las operaciones asincrónicas y la `Windows::Foundation::AsyncStatus` enumeración.|

### <a name="functions"></a>Funciones

|Name|Descripción|
|----------|-----------------|
|[ActivationFactoryCallback (función)](activationfactorycallback-function.md)|Obtiene el generador de activación para el identificador de activación especificado.|
|[Move (función)](move-function.md)|Mueve el argumento especificado de una ubicación a otra.|
|[RaiseException (función)](raiseexception-function.md)|Genera una excepción en el subproceso de llamada.|
|[Swap (función) (WRL)](swap-function-wrl.md)|Intercambia los valores de los dos argumentos especificados.|
|[TerminateMap (función)](terminatemap-function.md)|Cierra los generadores de clases en el módulo especificado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers (espacio de nombres)](microsoft-wrl-wrappers-namespace.md)