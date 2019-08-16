---
title: Import (C++ atributo com)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: f9ed80bdcc04302c0dee85935f377c8e3dbfd37f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514621"
---
# <a name="import"></a>importación

Especifica otro archivo. idl,. ODL o de encabezado que contiene las definiciones a las que se desea hacer referencia desde el IDL principal.

## <a name="syntax"></a>Sintaxis

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>Parámetros

*idl_file*<br/>
El nombre de un archivo. idl que desea importar en la biblioteca de tipos del proyecto actual.

## <a name="remarks"></a>Comentarios

El atributo **Import** C++ hace que `#import` se coloque una instrucción debajo de `import "docobj.idl"` la instrucción en el archivo. idl generado. El atributo de **importación** tiene la misma funcionalidad que el atributo MIDL de [importación](/windows/win32/Midl/import) .

El atributo **Import** solo coloca el archivo especificado en el archivo. idl que generará el proyecto; el atributo **Import** no permite llamar a las construcciones del archivo especificado a partir del código fuente del proyecto.  Para llamar a las construcciones del archivo especificado desde el código fuente del proyecto, use [#import](../../preprocessor/hash-import-directive-cpp.md) y el `embedded_idl` atributo, o bien puede incluir el archivo. h para *idl_file*, si existe un archivo. h.

## <a name="example"></a>Ejemplo

El código siguiente:

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

genera el siguiente código en el archivo. idl generado:

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
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)