---
title: Exportar (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.export
dev_langs:
- C++
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1529f6d43c3a4543a172229abe2adf0ce6a99c49
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060200"
---
# <a name="export"></a>exportar

Hace que una estructura de datos que se colocarán en el archivo. idl.

## <a name="syntax"></a>Sintaxis

```cpp
[export]
```

## <a name="remarks"></a>Comentarios

El **exportar** una estructura de datos que se colocarán en el archivo .idl y esté disponible en la biblioteca de tipos en un formato compatible con el archivo binario que hace que esté disponible para su uso con cualquier lenguaje hace que el atributo de C++.

No se puede aplicar el **exportar** atributo a una clase, incluso si la clase sólo tiene miembros públicos (el equivalente de un **struct**).

Si exporta una sin nombre **enum** o **struct**, se le asigna un nombre que comienza con **__unnamed**<em>x</em>, donde *x* es un número secuencial.

Las definiciones de tipo válidos para la exportación son tipos base, estructuras, uniones, enumeraciones, o escriba los identificadores.  Consulte [typedef](/windows/desktop/Midl/typedef) para obtener más información.

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo usar el **exportar** atributo:

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**Unión**, **typedef**, **enum**, **struct**, o **interfaz**|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)