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
ms.openlocfilehash: 220adeb44e676937756cf8007647f7e381f7607f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597565"
---
# <a name="out-c"></a>out (C++)

Identifica los parámetros de puntero devueltos desde el procedimiento llamado al procedimiento que realiza la llamada (desde el servidor al cliente).

## <a name="syntax"></a>Sintaxis

```cpp
[out]
```

## <a name="remarks"></a>Comentarios

El atributo de C++ **out** tiene la misma funcionalidad que el atributo MIDL [out](http://msdn.microsoft.com/library/windows/desktop/aa367136) .

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

[Atributos IDL](../windows/idl-attributes.md)  
[Atributos de parámetro](../windows/parameter-attributes.md)  
[defaultvalue](../windows/defaultvalue.md)  
[identificador](../windows/id.md)  