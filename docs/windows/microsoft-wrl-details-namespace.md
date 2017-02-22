---
title: "Microsoft::WRL::Details (Espacio de nombres) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Microsoft::WRL::Details (Espacio de nombres)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace Microsoft::WRL::Details;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="classes"></a>Clases  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[ComPtrRef (clase)](../Topic/ComPtrRef%20Class.md)|Representa una referencia a un objeto de tipo ComPtr \< T>.|  
|[ComPtrRefBase (clase)](../windows/comptrrefbase-class.md)|Representa la clase base para la [ComPtrRef](../Topic/ComPtrRef%20Class.md) clase.|  
|[DontUseNewUseMake (clase)](../windows/dontusenewusemake-class.md)|Impide el uso de operador `new` en `RuntimeClass`. Por consiguiente, debe utilizar el [función](../windows/make-function.md) en su lugar.|  
|[EventTargetArray (clase)](../windows/eventtargetarray-class.md)|Representa una matriz de controladores de eventos.|  
|[MakeAllocator (clase)](../windows/makeallocator-class.md)|Asigna memoria para una clase activable, con o sin compatibilidad con referencia débil.|  
|[ModuleBase (clase)](../windows/modulebase-class.md)|Representa la clase base de la [módulo](../windows/module-class.md) clases.|  
|[RemoveIUnknown (clase)](../windows/removeiunknown-class.md)|Convierte un tipo que es equivalente a un `IUnknown`-según tipo, pero tiene no virtual `QueryInterface`, `AddRef`, y `Release` métodos.|  
|[WeakReference (clase)](../windows/weakreference-class1.md)|Representa un *referencia débil* que se puede utilizar con el tiempo de ejecución de Windows o componentes COM clásicos. Una referencia débil representa un objeto que puede ser o no accesible.|  
  
### <a name="structures"></a>Estructuras  
  
|Name|Descripción|  
|----------|-----------------|  
|[ArgTraits (estructura)](../windows/argtraits-structure.md)|Declara a un delegado especificado de interfaz y una función miembro anónimo que tiene un número especificado de parámetros.|  
|[ArgTraitsHelper (estructura)](../windows/argtraitshelper-structure.md)|Ayuda a define las características comunes de los argumentos de delegado.|  
|[BoolStruct (estructura)](../windows/boolstruct-structure.md)|Define si un ComPtr administra la duración de los objetos de una interfaz. BoolStruct se utiliza internamente por el [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operador.|  
|[CreatorMap (estructura)](../windows/creatormap-structure.md)|Contiene información acerca de cómo inicializar, registrar y anular el registro de objetos.|  
|[DerefHelper (estructura)](../Topic/DerefHelper%20Structure.md)|Representa un puntero sin referencia a la `T*` parámetro de plantilla.|  
|[EnableIf (estructura)](../windows/enableif-structure.md)|Define un miembro de datos del tipo especificado por el segundo parámetro de plantilla si se evalúa como el primer parámetro de plantilla `true`.|  
|[FactoryCache (estructura)](../Topic/FactoryCache%20Structure.md)|Contiene la ubicación de un generador de clases y un valor que identifica un registrado [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] u objeto de clase COM.|  
|[ImplementsBase (estructura)](../windows/implementsbase-structure.md)|Utilizado para validar los tipos de parámetro de plantilla en [estructura implementa](../Topic/Implements%20Structure.md).|  
|[ImplementsHelper (estructura)](../windows/implementshelper-structure.md)|Ayuda a implementar la [implementa](../Topic/Implements%20Structure.md) estructura.|  
|[InterfaceList (estructura)](../windows/interfacelist-structure.md)|Se utiliza para crear una lista recursiva de interfaces.|  
|[InterfaceListHelper (estructura)](../Topic/InterfaceListHelper%20Structure.md)|Compila un `InterfaceList` tipo mediante la aplicación de los argumentos de parámetro de plantilla especificado recursiva.|  
|[InterfaceTraits (estructura)](../windows/interfacetraits-structure.md)|Características comunes de implementa de una interfaz.|  
|[InvokeHelper (estructura)](../windows/invokehelper-structure.md)|Proporciona una implementación del método Invoke() según el número especificado y el tipo de argumentos.|  
|[IsBaseOfStrict (estructura)](../windows/isbaseofstrict-structure.md)|Comprueba si un tipo es la base de otro.|  
|[IsSame (estructura)](../windows/issame-structure.md)|Comprueba si un tipo de especificado es igual que otro tipo especificado.|  
|[Nil (estructura)](../Topic/Nil%20Structure.md)|Se utiliza para indicar un parámetro de plantilla sin especificar, opcional.|  
|[RemoveReference (estructura)](../windows/removereference-structure.md)|Elimina el rasgo de referencia o referencia rvalue del parámetro de plantilla de clase especificada.|  
|[RuntimeClassBase (estructura)](../windows/runtimeclassbase-structure.md)|Permite detectar `RuntimeClass` en el [hacer](../windows/make-function.md) (función).|  
|[RuntimeClassBaseT (estructura)](../windows/runtimeclassbaset-structure.md)|Proporciona métodos auxiliares para `QueryInterface` operaciones y obtener identificadores de interfaz.|  
|[VerifyInheritanceHelper (estructura)](../windows/verifyinheritancehelper-structure.md)|Comprueba si una interfaz se deriva de otra interfaz.|  
|[VerifyInterfaceHelper (estructura)](../windows/verifyinterfacehelper-structure.md)|Comprueba que la interfaz especificada por el parámetro de plantilla cumple determinados requisitos.|  
  
### <a name="enumerations"></a>Enumeraciones  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[AsyncStatusInternal (enumeración)](../windows/asyncstatusinternal-enumeration.md)|Especifica una asignación entre enumeraciones internas para el estado de las operaciones asincrónicas y **Windows::Foundation::AsyncStatus** (enumeración).|  
  
### <a name="functions"></a>Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[ActivationFactoryCallback (función)](../windows/activationfactorycallback-function.md)|Obtiene el generador de activación para el identificador de activación especificado.|  
|[Move (función)](../Topic/Move%20Function.md)|Mueve el argumento especificado de una ubicación a otra.|  
|[RaiseException (función)](../windows/raiseexception-function.md)|Genera una excepción en el subproceso de llamada.|  
|[Swap (función) (biblioteca de plantillas de C++ en tiempo de ejecución de Windows)](../windows/swap-function-windows-runtime-cpp-template-library.md)|Intercambia los valores de los dos argumentos especificados.|  
|[TerminateMap (función)](../windows/terminatemap-function.md)|Cierra los generadores de clases en el módulo especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h  
  
 **Espacio de nombres:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres Microsoft:: wrl](../windows/microsoft-wrl-namespace.md)   
 [Espacio de nombres Wrappers](../Topic/Microsoft::WRL::Wrappers%20Namespace.md)