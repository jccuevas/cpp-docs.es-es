---
title: Inspectableclass (macro) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 44bdcbc84a1ed2d57b0c9a0ce9eca4feebb0b133
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059706"
---
# <a name="inspectableclass-macro"></a>InspectableClass (Macro)

Establece el nivel de confianza y de nombre de clase en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>Parámetros

*runtimeClassName*<br/>
El nombre textual completo de la clase en tiempo de ejecución.

*trustLevel*<br/>
Uno de los [TrustLevel](https://msdn.microsoft.com/library/br224625.aspx) valores enumerados.

## <a name="remarks"></a>Comentarios

El **InspectableClass** macro puede utilizarse solo con tipos de Windows en tiempo de ejecución.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[RuntimeClass (clase)](../windows/runtimeclass-class.md)