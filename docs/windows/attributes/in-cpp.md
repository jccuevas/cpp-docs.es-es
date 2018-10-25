---
title: (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.in
dev_langs:
- C++
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d31de803e1a867c7a9e509ced71eb3801d3946ff
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066843"
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
[identificador](id.md)<br/>
[out](out-cpp.md)