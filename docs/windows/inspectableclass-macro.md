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
ms.openlocfilehash: 0a19635b635b80d65e0da99b8f50606154a5b4b2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594773"
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

*runtimeClassName*  
El nombre textual completo de la clase en tiempo de ejecución.

*trustLevel*  
Uno de los [TrustLevel](http://msdn.microsoft.com/library/br224625.aspx) valores enumerados.

## <a name="remarks"></a>Comentarios

El **InspectableClass** macro puede utilizarse solo con tipos de Windows en tiempo de ejecución.

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[RuntimeClass (clase)](../windows/runtimeclass-class.md)