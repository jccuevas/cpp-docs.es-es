---
title: operator== (&lt;sample container&gt;) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
dev_langs:
- C++
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 360c4f38b0c740d1c23b1fa9c0712eaf6657d495
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="operator-ltsample-containergt"></a>operator== (&lt;sample container&gt;)

> [!NOTE]
> Este tema se incluye en la documentación de Visual C++ como un ejemplo no funcional de los contenedores usados en la biblioteca estándar de C++. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

Sobrecarga `operator==` para comparar dos objetos de la clase de plantilla [Container](../standard-library/sample-container-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Valor devuelto

Devuelve `left.` [tamaño](../standard-library/container-class-size.md) ` == right.size && equal(left.` [comenzar](../standard-library/container-class-begin.md)`, left.`[final](../standard-library/container-class-end.md)`, right.begin)`.

## <a name="see-also"></a>Vea también

[\<sample container>](../standard-library/sample-container.md)<br/>
