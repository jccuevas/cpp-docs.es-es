---
title: '&lt;typeindex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <typeindex>
dev_langs:
- C++
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 189fb7cd3757a3f71a50badc682b7b4db611b4e0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855115"
---
# <a name="lttypeindexgt"></a>&lt;typeindex&gt;

Incluya el encabezado estándar \<typeindex > para definir una clase y función que admitan la indización de objetos de clase [type_info](../cpp/type-info-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
#include <typeindex>
```

## <a name="remarks"></a>Comentarios

La [estructura hash](../standard-library/hash-structure.md) define una `hash function` adecuada para asignar valores de tipo [type_index](../standard-library/type-index-class.md) a una distribución de valores de índice.

La clase `type_index` encapsula un puntero a un objeto `type_info` para facilitar la indización.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
