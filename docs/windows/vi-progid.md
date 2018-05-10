---
title: vi_progid | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.vi_progid
dev_langs:
- C++
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 687a8a70d7f0a5381160a6515c80f6940cc0a434
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="viprogid"></a>vi_progid
Especifica una forma independiente de la versión de ProgID.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ vi_progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 El ProgID independientes de la versión que representa el objeto.  
  
 ProgID presentan una versión legible del identificador de clase (CLSID) utilizado para identificar los objetos COM y ActiveX.  
  
## <a name="remarks"></a>Comentarios  
 El **vi_progid** atributo C++ permite especificar un ProgID independientes de la versión de un objeto COM. Un ProgID tiene la forma *name1.name2.version*. Un ProgID independientes de la versión no tiene un *versión*. Es posible especificar tanto el **progid** y **vi_progid** atributos en una coclase. Si no se especifica **vi_progid**, el ProgID independientes de la versión es el valor especificado por el [progid](../windows/progid.md) atributo.  
  
 **vi_progid** implica la **coclase** atributo, es decir, si especifica **vi_progid**, es lo mismo que especificar el **coclase** y **vi_progid** atributos.  
  
 El **vi_progid** atributo da lugar a una clase que se registren automáticamente con el nombre especificado. El archivo .idl generado no mostrará el valor de Id. de programa.  
  
 En los proyectos ATL, si la [coclase](../windows/coclass.md) atributo también está presente, se utiliza el ProgID especificado por el **GetVersionIndependentProgID** función (insertados por el **coclase** atributo).  
  
## <a name="example"></a>Ejemplo  
 Consulte la [coclase](../windows/coclass.md) ejemplo para un ejemplo de uso de **vi_progid**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**class**, `struct`|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributos de clase](../windows/class-attributes.md)   
 [Clave progID](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
