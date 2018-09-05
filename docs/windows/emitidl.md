---
title: emitidl | Microsoft Docs
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
ms.openlocfilehash: 7e1cb0a77c04a1bfea03f742686e1b28a6e2f04c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687855"
---
# <a name="emitidl"></a>emitidl

Especifica si se procesan todos los atributos IDL subsiguientes y se coloca en el archivo .idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>Parámetros

*state*  
Uno de estos valores posibles: `true`, `false`, `forced`, `restricted`, `push`, o `pop`.

- Si `true`, los atributos de la categoría IDL encontrado en un archivo de código fuente se colocan en el archivo .idl generado. Se trata de la configuración predeterminada de **emitidl**.

- Si `false`, los atributos de la categoría IDL encontrado en un archivo de código fuente no se colocan en el archivo .idl generado.

- Si `restricted`, permite que los atributos IDL en el archivo sin un [módulo](../windows/module-cpp.md) atributo. El compilador no genera un archivo. idl.

- Si `forced`, reemplaza un posteriores `restricted` atributo, que requiere un archivo para que tenga un `module` atributo si no hay IDL atributos en el archivo.

- `push` permite guardar actual **emitidl** configuración a una instancia interna **emitidl** pila, y `pop` permite establecer **emitidl** a cualquier valor es la parte superior de interno **emitidl** pila.

`defaultimports=`*booleano* \(opcional)  
- Si *booleano* es **true**, docobj.idl se importa en el archivo .idl generado. Además, si el archivo que un archivo .idl con el mismo nombre que un .h `#include` en el origen de código se encuentra en el mismo directorio que el archivo .h y, después, el archivo .idl generado contiene una instrucción de importación para ese archivo. idl.

- Si *booleano* es **false**, docobj.idl no se importa en el archivo .idl generado. Debe importar de forma explícita los archivos .idl con [importar](../windows/import.md).

## <a name="remarks"></a>Comentarios

Después de la **emitidl** atributo de C++ se encuentra en un archivo de código fuente, los atributos de categoría IDL se colocan en el archivo .idl generado. Si no hay ningún **emitidl** atributo, el atributo IDL del archivo de código fuente son el resultado al archivo .idl generado.

Es posible tener varios **emitidl** atributos en un archivo de código fuente. Si `[emitidl(false)];` se encuentra en un archivo sin un posteriores `[emitidl(true)];`, a continuación, no se procesan atributos en el archivo .idl generado.

Cada vez que el compilador encuentra un nuevo archivo, **emitidl** se establece implícitamente en **true**.

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
