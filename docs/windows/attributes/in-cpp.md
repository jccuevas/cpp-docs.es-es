---
title: (atributo de COM de C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: 06d78552ef2ebb878ed630eb377e6249ba60cad4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034542"
---
# <a name="in-c"></a>in (C++)

Indica que es un parámetro que se pasan desde el procedimiento que realiza la llamada al procedimiento llamado.

## <a name="syntax"></a>Sintaxis

```cpp
[in]
```

## <a name="remarks"></a>Comentarios

El **en** atributo de C++ tiene la misma funcionalidad que el [en](/windows/desktop/Midl/in) atributo MIDL.

## <a name="example"></a>Ejemplo

Consulte [enlazable](bindable.md) para obtener un ejemplo de cómo usar **en**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz, el método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|**retval**|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)