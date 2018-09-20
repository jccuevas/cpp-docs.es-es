---
title: reemplaza a typeof | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4433061fceef455685b6588c81c8c2e434253433
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374685"
---
# <a name="typeof-goes-to-ttypeid"></a>T::typeid reemplaza typeof

El `typeof` operador usado en extensiones administradas para C++ ha suplantado por el `typeid` palabra clave en Visual C++.

En extensiones administradas, el `__typeof()` operador devuelve asociado `Type*` objeto cuando se pasa el nombre de un tipo administrado. Por ejemplo:

```
// Creates and initializes a new Array instance.
Array* myIntArray =
   Array::CreateInstance( __typeof(Int32), 5 );
```

En la nueva sintaxis, `__typeof` ha sido reemplazado por un método adicional de `typeid` que devuelve un `Type^` cuando se especifica un tipo administrado.

```
// Creates and initializes a new Array instance.
Array^ myIntArray =
   Array::CreateInstance( Int32::typeid, 5 );
```

## <a name="see-also"></a>Vea también

[Cambios generales en el lenguaje (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[typeid](../windows/typeid-cpp-component-extensions.md)