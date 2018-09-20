---
title: en (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: cd6b79d84e4737cdbeb670bdd31b8cacf35cf8f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373392"
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

Consulte [enlazable](../windows/bindable.md) para obtener un ejemplo de cómo usar **en**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|Parámetro de interfaz, el método de interfaz|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|**retval**|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos IDL](../windows/idl-attributes.md)<br/>
[Atributos de parámetro](../windows/parameter-attributes.md)<br/>
[Atributos de método](../windows/method-attributes.md)<br/>
[defaultvalue](../windows/defaultvalue.md)<br/>
[identificador](../windows/id.md)<br/>
[out](../windows/out-cpp.md)  