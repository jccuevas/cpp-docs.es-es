---
title: UUID (atributos de C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.uuid
dev_langs:
- C++
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ba35dc89ae2567a499d4623f0c74293d2dbdcca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="uuid-c-attributes"></a>uuid (Atributos de C++)
Especifica el identificador único para una clase o interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ uuid(  
   "uuid"  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *UUID*  
 Un identificador de 128 bits único.  
  
## <a name="remarks"></a>Comentarios  
 Si no especifica la definición de una interfaz o clase la `uuid` atributos de C++, el compilador de Visual C++ proporcionará uno. Cuando se especifica un `uuid`, debe incluir las comillas.  
  
 Si no se especifica `uuid`, el compilador generará el mismo GUID para las interfaces o clases con el mismo nombre en los proyectos de atributo diferente en un equipo.  
  
 Puede usar Uuidgen.exe o Guidgen.exe para generar sus propios identificadores únicos. (Para ejecutar cualquiera de estas herramientas, haga clic en **iniciar** y haga clic en **ejecutar** en el menú. A continuación, escriba el nombre de la herramienta necesaria.)  
  
 Cuando se utiliza en un proyecto que no utilizar ATL, especificando el `uuid` atributo es lo mismo que especificar el [uuid](../cpp/uuid-cpp.md) __declspec (modificador). Para recuperar el `uuid` de una clase, que se puede usar [__uuidof](../cpp/uuidof-operator.md)  
  
## <a name="example"></a>Ejemplo  
 Consulte la [enlazables](../windows/bindable.md) ejemplo para un ejemplo de uso de `uuid`.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`, `interface`, **union**,`enum`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos de interfaz](../windows/interface-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [UUID](http://msdn.microsoft.com/library/windows/desktop/aa367302)   
