---
title: subprocesamiento (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.threading
dev_langs:
- C++
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f21ea8c16b4e09a5ad1845a10797be00f91b0d8f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891329"
---
# <a name="threading-c"></a>threading (C++)
Especifica el modelo de subprocesos de un objeto COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ threading(  
   model=enumeration  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 ***modelo*** (opcional)  
 Uno de los siguientes modelos de subprocesamiento:  
  
-   **apartamento** (apartamento de subproceso)  
  
-   **neutro** (componentes de .NET Framework sin interfaz de usuario)  
  
-   **solo** (ejecución de subprocesos simple)  
  
-   **libre** (libre de subprocesos)  
  
-   **ambos** (apartamento y subprocesamiento libre)  
  
 El valor predeterminado es **apartamento**.  
  
## <a name="remarks"></a>Comentarios  
 El **subprocesamiento** atributo C++ no aparece en el archivo .idl generado, pero se utilizarán en la implementación del objeto COM.  
  
 En los proyectos ATL, si la [coclase](../windows/coclass.md) también está presente, el atributo especificado por el modelo de subprocesamiento *modelo* se pasa como el parámetro de plantilla para la [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) (clase) , inserta la **coclase** atributo.  
  
 El **subprocesamiento** atributo también evita el acceso a un [event_source](../windows/event-source.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte la [con licencia](../windows/licensed.md) ejemplo para un ejemplo de uso de **subprocesamiento**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**class**, `struct`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|**coclass**|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos COM](../windows/com-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [Compatibilidad con multithreading código antiguo (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [Neutros apartamentos](http://msdn.microsoft.com/library/windows/desktop/ms681813)   
