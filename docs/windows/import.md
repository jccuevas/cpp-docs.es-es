---
title: importar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.import
dev_langs:
- C++
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78bfc20bd88aa9691c80483c8c315cd5305d7b96
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216596"
---
# <a name="import"></a>importación

Especifica otro archivo .idl, .odl o encabezado que contiene las definiciones que desea hacer referencia desde la principal IDL.

## <a name="syntax"></a>Sintaxis

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>Parámetros

*idl_file*  
El nombre de un archivo .idl que desea importar en la biblioteca de tipos del proyecto actual.

## <a name="remarks"></a>Comentarios

El **importar** hace que el atributo de C++ un `#import` instrucción colocarse debajo el `import "docobj.idl"` instrucción en el archivo .idl generado. El **importar** atributo tiene la misma funcionalidad que el [importar](/windows/desktop/Midl/import) atributo MIDL.

El **importar** atributo sólo coloca el archivo especificado en el archivo .idl que se generará el proyecto; el **importar** atributo no le permite llamar a construcciones en el archivo especificado desde el código fuente en el proyecto.  Para llamar a construcciones en el archivo especificado desde el código fuente en el proyecto, utilice [#import](../preprocessor/hash-import-directive-cpp.md) y `embedded_idl` atributo, o bien puede incluir el archivo .h el *idl_file*, si existe un archivo .h.

## <a name="example"></a>Ejemplo

El código siguiente:

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

genera el código siguiente en el archivo .idl generado:

```
import "docobj.idl";
import "import.idl";

[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]
library MyLib {
   importlib("stdole2.tlb");
   importlib("olepro32.dll");
...
```

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

[Atributos IDL](../windows/idl-attributes.md)  
[Atributos independientes](../windows/stand-alone-attributes.md)  
[importidl](../windows/importidl.md)  
[importlib](../windows/importlib.md)  
[include](../windows/include-cpp.md)  
[includelib](../windows/includelib-cpp.md)  