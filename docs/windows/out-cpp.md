---
title: out (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.out
dev_langs:
- C++
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1b90222faedf298f75bfea72c661a3f23f26eaed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394894"
---
# <a name="out-c"></a>out (C++)

Identifica los parámetros de puntero devueltos desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).

## <a name="syntax"></a>Sintaxis

```cpp
[out]
```

## <a name="remarks"></a>Comentarios

El **out** atributo de C++ tiene la misma funcionalidad que el [out](/windows/desktop/Midl/out-idl) atributo MIDL.

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [bindable](../windows/bindable.md) para ver un ejemplo de uso de **out**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de parámetro](../windows/parameter-attributes.md)<br/>
[defaultvalue](../windows/defaultvalue.md)<br/>
[identificador](../windows/id.md)  