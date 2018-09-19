---
title: versión (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87186ee70b5863f51a7cd91f8695052f361bd11c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222537"
---
# <a name="version-c"></a>version (C++)

Identifica una versión determinada entre varias versiones de una clase.

## <a name="syntax"></a>Sintaxis

```cpp
[ version(
   "version"
) ]
```

### <a name="parameters"></a>Parámetros

*version*  
El número de versión de la `coclass`. Si no se especifica, se colocará en el archivo .idl 1.0.

## <a name="remarks"></a>Comentarios

El **versión** atributo de C++ tiene la misma funcionalidad que el [versión](/windows/desktop/Midl/version) atributo MIDL y se pasa a través del archivo .idl generado.

## <a name="example"></a>Ejemplo

Consulte la [enlazable](../windows/bindable.md) ejemplo para un ejemplo de uso de **versión**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|**clase**, **struct**|
|**Reiterativo**|No|
|**Atributos requeridos**|**coclass**|
|**Atributos no válidos**|Ninguna|

Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).

## <a name="see-also"></a>Vea también

[Atributos de compilador](../windows/compiler-attributes.md)  
[Atributos de clase](../windows/class-attributes.md)  