---
title: Id. de programa | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2b2d2168b568c74c5404cc83bab1e5f77570773
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880438"
---
# <a name="progid"></a>progid
Especifica el ProgID de un objeto COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 El ProgID que representa el objeto.  
  
 ProgID presentan una versión legible del identificador de clase (CLSID) utilizado para identificar los objetos COM y ActiveX.  
  
## <a name="remarks"></a>Comentarios  
 El **progid** atributo C++ le permite especificar el ProgID de un objeto COM. Un ProgID tiene la forma *name1.name2.version*. Si no especifica un *versión* para un ProgID, la versión predeterminada es 1. Si no se especifica *name1.name2*, el nombre predeterminado es *classname.classname*. Si no se especifica **progid** y especifique **vi_progid**, *name1.name2* se toman de **vi_progid** y (siguiente secuencial se anexa versión número).  
  
 Si un bloque de atributos que usa **progid** no usar `uuid`, el compilador comprobará el registro para ver si un `uuid` existe para el elemento especificado **progid**. Si **progid** no se especifica, se usará la versión (y el nombre de la coclase, si la creación de una coclase) para generar un **progid**.  
  
 **Id. de programa** implica la **coclase** atributo, es decir, si especifica **progid**, es lo mismo que especificar el **coclase** y  **Id. de programa** atributos.  
  
 El **progid** atributo da lugar a una clase que se registren automáticamente con el nombre especificado. No se mostrará el archivo .idl generado el **progid** valor.  
  
 Cuando este atributo se utiliza dentro de un proyecto que usa ATL, cambia el comportamiento del atributo. Además el comportamiento anterior, se utiliza la información especificada por este atributo en el **GetProgID** función, insertado por el **coclase** atributo. Para obtener más información, consulte el [coclase](../windows/coclass.md) atributo.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [coclase](../windows/coclass.md) para un ejemplo de uso de **progid**.  
  
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
 [Atributos de clase](../windows/class-attributes.md)   
 [TypeDef, Enum, Union y Struct (atributos)](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Clave progID](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
