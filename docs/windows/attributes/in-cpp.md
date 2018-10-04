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
ms.openlocfilehash: 31c47fa07375c587257bc979ac68b64381880398
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792128"
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

Para obtener más información acerca de los contextos de atributo, vea [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos de parámetro](parameter-attributes.md)<br/>
[Atributos de método](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[identificador](id.md)<br/>
[out](out-cpp.md)  