---
title: Export (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 771bfdfe4eab2acf31e97a606795066e8938a8a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501601"
---
# <a name="export"></a>exportar

Hace que una estructura de datos se coloque en el archivo. idl.

## <a name="syntax"></a>Sintaxis

```cpp
[export]
```

## <a name="remarks"></a>Comentarios

El atributo **Export** C++ hace que se coloque una estructura de datos en el archivo. idl y que, a continuación, esté disponible en la biblioteca de tipos en un formato compatible con binario que permita su uso con cualquier lenguaje.

No se puede aplicar el atributo **Export** a una clase aunque la clase solo tenga miembros públicos (el equivalente de un **struct**).

Si exporta una enumeración o un **struct**sin nombre, se le asigna un nombre que comienza por **__unnamed**<em>x</em>, donde *x* es un número secuencial.

Las definiciones de tipo válidas para la exportación son tipos base, Structs, uniones, enumeraciones o identificadores de tipo.  Vea [typedef](/windows/win32/Midl/typedef) para obtener más información.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo usar el atributo **Export** :

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
|**Se aplica a**|**Union**, **typedef**, **enum**, **struct**o **interface**|
|**Reiterativo**|Sin|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos de compilador](compiler-attributes.md)<br/>
[Typedef, Enum, Union y Struct (atributos)](typedef-enum-union-and-struct-attributes.md)