---
title: Threading (C++) | Microsoft Docs
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
ms.openlocfilehash: d6da3bd5f0dd318b781d967d7974ef603b60b9ad
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019207"
---
# <a name="threading-c"></a>threading (C++)
Especifica el modelo de subprocesos para un objeto COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
[ threading(  
   model=enumeration  
) ]  
```  
  
### <a name="parameters"></a>Parámetros  
 *modelo* (opcional)  
 Uno de los modelos de subprocesamiento siguientes:  
  
-   `apartment` (apartamento de subproceso)  
  
-   `neutral` (Componentes de .NET framework sin interfaz de usuario)  
  
-   `single` (ejecución de subprocesos simple)  
  
-   `free` (subprocesamiento libre)  
  
-   `both` (apartamento y subprocesamiento libre)  
  
 El valor predeterminado es `apartment`.  
  
## <a name="remarks"></a>Comentarios  
 El **threading** atributo de C++ no aparece en el archivo .idl generado, pero se utilizará en la implementación de su objeto COM.  
  
 En los proyectos ATL, si la [coclase](../windows/coclass.md) también está presente, el atributo especificado por el modelo de subprocesos *modelo* se pasa como parámetro de plantilla para el [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) clase , inserta el `coclass` atributo.  
  
 El **threading** atributo también protege el acceso a un [event_source](../windows/event-source.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte la [licencia](../windows/licensed.md) ejemplo para un ejemplo de uso de **threading**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, **struct**|  
|**Reiterativo**|No|  
|**Atributos requeridos**|**coclass**|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos COM](../windows/com-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [Compatibilidad con multithreading código antiguo (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [Apartamentos neutros](http://msdn.microsoft.com/library/windows/desktop/ms681813)   