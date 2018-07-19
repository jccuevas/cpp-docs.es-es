---
title: emitidl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.emitidl
dev_langs:
- C++
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e4c66ba8c49a405f9fdd93b1652626ab47488a53
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876597"
---
# <a name="emitidl"></a>emitidl
Especifica si todos los atributos IDL posteriores se procesan y se colocan en el archivo .idl generado.  
  
## <a name="syntax"></a>Sintaxis  
  
```
[ emitidl(state, defaultimports=boolean) ];
```  
  
### <a name="parameters"></a>Parámetros  
*state*  
Uno de estos valores posibles: **true**, **false**, **forzado**, **restringido**, **inserción**, o **pop**.  
  
-   Si **true**, los atributos de categoría IDL encontrados en un archivo de código fuente se colocan en el archivo .idl generado. Ésta es la configuración predeterminada para **emitidl**.  
  
-   Si **false**, los atributos de categoría IDL encontrados en un archivo de código fuente no se colocan en el archivo .idl generado.  
  
-   Si **restringido**, permite que los atributos IDL en el archivo sin una [módulo](../windows/module-cpp.md) atributo. El compilador no genera un archivo IDL.  
  
-   Si **forzado**, invalida una posterior **restringido** atributo, que requiere un archivo para que tenga un **módulo** atributo si hay IDL atributos en el archivo.  
  
-   **inserción** permite guardar actual **emitidl** configuración un interno **emitidl** pila, y **pop** permite establecer **emitidl**con cualquier valor se encuentra en la parte superior de la interna **emitidl** pila.  
  
`defaultimports=`*booleano* \(opcional)  
-   Si *booleano* es **true**, docobj.idl se importan en el archivo .idl generado. Además, si un archivo .idl con el mismo nombre que un .h archivo que `#include` en el origen de código se encuentra en el mismo directorio que el archivo .h, a continuación, el archivo .idl generado contiene una instrucción de importación para ese archivo IDL.  
  
-   Si *booleano* es **false**, docobj.idl no se importa en el archivo .idl generado. Debe importar de forma explícita los archivos .idl con [importar](../windows/import.md).  
  
## <a name="remarks"></a>Comentarios  
Después de la **emitidl** atributo de C++ se encuentra en un archivo de código fuente, los atributos de categoría IDL se colocan en el archivo .idl generado. Si no hay ningún **emitidl** salen de atributo, los atributos IDL en el archivo de código fuente en el archivo .idl generado.  
  
Es posible tener varios **emitidl** atributos en un archivo de código fuente. Si `[emitidl(false)];` se encuentra en un archivo sin una posterior `[emitidl(true)];`, entonces no se procesa ningún atributo en el archivo .idl generado.  
  
Cada vez que el compilador encuentra un archivo nuevo, **emitidl** se establece implícitamente en **true**.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|En cualquier lugar|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
[Atributos de compilador](../windows/compiler-attributes.md)   
[Atributos independientes](../windows/stand-alone-attributes.md)   
[Ejemplos de atributos](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)