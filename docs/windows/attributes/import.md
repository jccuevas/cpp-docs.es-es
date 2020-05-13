---
title: Import (C++ atributo com)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: f2a0aa9a68c081e83a7a5278aa37a7fddac85416
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166841"
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

## <a name="remarks"></a>Observaciones

El atributo **Import** C++ hace que se coloque una instrucción `#import` debajo de la instrucción `import "docobj.idl"` en el archivo. idl generado. El atributo de **importación** tiene la misma funcionalidad que el atributo MIDL de [importación](/windows/win32/Midl/import) .

El atributo **Import** solo coloca el archivo especificado en el archivo. idl que generará el proyecto; el atributo **Import** no permite llamar a las construcciones del archivo especificado a partir del código fuente del proyecto.  Para llamar a las construcciones del archivo especificado a partir del código fuente del proyecto, use [#import](../../preprocessor/hash-import-directive-cpp.md) y el atributo `embedded_idl`, o bien puede incluir el archivo. h para el *idl_file*si existe un archivo. h.

## <a name="example"></a>Ejemplo

En el código siguiente:

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
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
