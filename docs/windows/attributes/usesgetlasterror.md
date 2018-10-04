---
title: usesgetlasterror (atributo de COM de C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.usesgetlasterror
dev_langs:
- C++
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 501f6b1801ace9f6002cca5d3559dfcb01e994f5
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48792162"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Indica que el llamador que si se produce un error al llamar a esa función, a continuación, el llamador puede, a continuación, llamar a `GetLastError` para recuperar el código de error.

## <a name="syntax"></a>Sintaxis

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Comentarios

El **usesgetlasterror** atributo de C++ tiene la misma funcionalidad que el [usesgetlasterror](/windows/desktop/Midl/usesgetlasterror) atributo MIDL.

## <a name="example"></a>Ejemplo

Consulte la [idl_module](idl-module.md) ejemplo para obtener un ejemplo de cómo usar **usesgetlasterror**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**módulo** atributo|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, vea [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)  