---
title: emitidl (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.emitidl
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
ms.openlocfilehash: 6c4055e0f14bced1e5047fc502a4bf274126f804
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031639"
---
# <a name="emitidl"></a>emitidl

Especifica si se procesan todos los atributos IDL subsiguientes y se coloca en el archivo .idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Uno de estos valores posibles: `true`, `false`, `forced`, `restricted`, `push`, o `pop`.

- Si `true`, los atributos de la categoría IDL encontrado en un archivo de código fuente se colocan en el archivo .idl generado. Se trata de la configuración predeterminada de **emitidl**.

- Si `false`, los atributos de la categoría IDL encontrado en un archivo de código fuente no se colocan en el archivo .idl generado.

- Si `restricted`, permite que los atributos IDL en el archivo sin un [módulo](module-cpp.md) atributo. El compilador no genera un archivo. idl.

- Si `forced`, reemplaza un posteriores `restricted` atributo, que requiere un archivo para que tenga un `module` atributo si no hay IDL atributos en el archivo.

- `push` permite guardar actual **emitidl** configuración a una instancia interna **emitidl** pila, y `pop` permite establecer **emitidl** a cualquier valor es la parte superior de interno **emitidl** pila.

`defaultimports=`*booleano* \(opcional)

- Si *booleano* es **true**, docobj.idl se importa en el archivo .idl generado. Además, si el archivo que un archivo .idl con el mismo nombre que un .h `#include` en el origen de código se encuentra en el mismo directorio que el archivo .h y, después, el archivo .idl generado contiene una instrucción de importación para ese archivo. idl.

- Si *booleano* es **false**, docobj.idl no se importa en el archivo .idl generado. Debe importar de forma explícita los archivos .idl con [importar](import.md).

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

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)
