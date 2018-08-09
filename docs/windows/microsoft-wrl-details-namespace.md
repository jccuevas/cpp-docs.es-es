---
title: Wrl Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9effc65b150c68a5191712b364c80ad42dd276ad
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012133"
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
|[ComPtrRef (clase)](../windows/comptrref-class.md)|Representa una referencia a un objeto de tipo ComPtr\<T >.|  
|[ComPtrRefBase (clase)](../windows/comptrrefbase-class.md)|Representa la clase base para el [ComPtrRef](../windows/comptrref-class.md) clase.|  
|[DontUseNewUseMake (clase)](../windows/dontusenewusemake-class.md)|Impide el uso de operador **nueva** en `RuntimeClass`. Por lo tanto, debe usar el [función](../windows/make-function.md) en su lugar.|  
|[EventTargetArray (clase)](../windows/eventtargetarray-class.md)|Representa una matriz de controladores de eventos.|  
|[MakeAllocator (clase)](../windows/makeallocator-class.md)|Asigna memoria para una clase activable, con o sin compatibilidad con la referencia débil.|  
|[ModuleBase (clase)](../windows/modulebase-class.md)|Representa la clase base de la [módulo](../windows/module-class.md) clases.|  
|[RemoveIUnknown (clase)](../windows/removeiunknown-class.md)|Convierte un tipo que es equivalente a un `IUnknown`-tipo de función, pero tiene no virtual `QueryInterface`, `AddRef`, y `Release` métodos.|  
|[WeakReference (clase)](../windows/weakreference-class1.md)|Representa un *referencia débil* que puede utilizarse con el tiempo de ejecución de Windows o COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.|  
  
### <a name="structures"></a>Estructuras  
  
|Name|Descripción|  
|----------|-----------------|  
|[ArgTraits (estructura)](../windows/argtraits-structure.md)|Interfaz y una función miembro anónimo que tiene un número especificado de parámetros se declara a un delegado especificado.|  
|[ArgTraitsHelper (estructura)](../windows/argtraitshelper-structure.md)|Ayuda a define las características comunes de los argumentos de delegado.|  
|[BoolStruct (estructura)](../windows/boolstruct-structure.md)|Define si un `ComPtr` administra la duración del objeto de una interfaz. `BoolStruct` se usa internamente el [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operador.|  
|[CreatorMap (estructura)](../windows/creatormap-structure.md)|Contiene información acerca de cómo inicializar, registrar y anular el registro de objetos.|  
|[DerefHelper (estructura)](../windows/derefhelper-structure.md)|Representa un puntero sin referencia a la `T*` parámetro de plantilla.|  
|[EnableIf (estructura)](../windows/enableif-structure.md)|Define un miembro de datos del tipo especificado por el segundo parámetro de plantilla si se evalúa como el primer parámetro de plantilla **true**.|  
|[FactoryCache (estructura)](../windows/factorycache-structure.md)|Contiene la ubicación de un generador de clases y un valor que identifica un objeto de clase en tiempo de ejecución de Windows o COM registrado.|  
|[ImplementsBase (estructura)](../windows/implementsbase-structure.md)|Utilizado para validar los tipos de parámetro de plantilla en [Implements (estructura)](../windows/implements-structure.md).|  
|[ImplementsHelper (estructura)](../windows/implementshelper-structure.md)|Ayuda a implementar la [implementa](../windows/implements-structure.md) estructura.|  
|[InterfaceList (estructura)](../windows/interfacelist-structure.md)|Se utiliza para crear una lista recursiva de las interfaces.|  
|[InterfaceListHelper (estructura)](../windows/interfacelisthelper-structure.md)|Compila una `InterfaceList` tipo mediante la aplicación de los argumentos de parámetro de plantilla especificado recursiva.|  
|[InterfaceTraits (estructura)](../windows/interfacetraits-structure.md)|Características comunes de implementa de una interfaz.|  
|[InvokeHelper (estructura)](../windows/invokehelper-structure.md)|Proporciona una implementación de la `Invoke()` método según el número especificado y el tipo de argumentos.|  
|[IsBaseOfStrict (estructura)](../windows/isbaseofstrict-structure.md)|Comprueba si un tipo es la base de otro.|  
|[IsSame (estructura)](../windows/issame-structure.md)|Las pruebas si un tipo especificado es igual que otro tipo especificado.|  
|[Nil (estructura)](../windows/nil-structure.md)|Se utiliza para indicar un parámetro de plantilla opcional no especificado.|  
|[RemoveReference (estructura)](../windows/removereference-structure.md)|Elimina el rasgo de referencia o referencia de rvalue desde el parámetro de plantilla de clase especificada.|  
|[RuntimeClassBase (estructura)](../windows/runtimeclassbase-structure.md)|Utilizado para detectar `RuntimeClass` en el [realizar](../windows/make-function.md) función.|  
|[RuntimeClassBaseT (estructura)](../windows/runtimeclassbaset-structure.md)|Proporciona métodos auxiliares para `QueryInterface` operaciones y obtener los identificadores de interfaz.|  
|[VerifyInheritanceHelper (estructura)](../windows/verifyinheritancehelper-structure.md)|Comprueba si una interfaz se deriva de otra interfaz.|  
|[VerifyInterfaceHelper (estructura)](../windows/verifyinterfacehelper-structure.md)|Comprueba que la interfaz especificada por el parámetro de plantilla cumple determinados requisitos.|  
  
### <a name="enumerations"></a>Enumeraciones  
  
|nombre|Descripción|  
|----------|-----------------|  
|[AsyncStatusInternal (enumeración)](../windows/asyncstatusinternal-enumeration.md)|Especifica una asignación entre enumeraciones internas para el estado de las operaciones asincrónicas y la `Windows::Foundation::AsyncStatus` enumeración.|  
  
### <a name="functions"></a>Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[ActivationFactoryCallback (función)](../windows/activationfactorycallback-function.md)|Obtiene el generador de activación para el identificador de activación especificado.|  
|[Move (función)](../windows/move-function.md)|Mueve el argumento especificado de una ubicación a otra.|  
|[RaiseException (función)](../windows/raiseexception-function.md)|Genera una excepción en el subproceso de llamada.|  
|[Swap (función) (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)](../windows/swap-function-windows-runtime-cpp-template-library.md)|Intercambia los valores de los dos argumentos especificados.|  
|[TerminateMap (función)](../windows/terminatemap-function.md)|Cierra los generadores de clases en el módulo especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft:: wrl Namespace](../windows/microsoft-wrl-namespace.md)   
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)