---
title: importidl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importidl
dev_langs:
- C++
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9406cc95804e4eb9fd76f53201118f13f0e422a4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410512"
---
# <a name="importidl"></a>importidl

Inserta el archivo .idl especificado en el archivo .idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ importidl(
   idl_file
) ];
```

### <a name="parameters"></a>Parámetros

*idl_file*<br/>
Identifica el nombre del archivo .idl que desea combinar con el archivo .idl que se generará para la aplicación.

## <a name="remarks"></a>Comentarios

El **importidl** atributo de C++ coloca la sección fuera del bloque de biblioteca (en *idl_file*) en el archivo .idl generado del programa y la sección de biblioteca (en *idl_file*) en la biblioteca de la sección de su programa genera el archivo .idl.

Es posible que desee usar **importidl**, por ejemplo, si desea usar un archivo .idl codificadas con el archivo .idl generado.

## <a name="example"></a>Ejemplo

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
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

[Atributos de compilador](../windows/compiler-attributes.md)<br/>
[Atributos independientes](../windows/stand-alone-attributes.md)<br/>
[import](../windows/import.md)<br/>
[importlib](../windows/importlib.md)<br/>
[include](../windows/include-cpp.md)<br/>
[includelib](../windows/includelib-cpp.md)  