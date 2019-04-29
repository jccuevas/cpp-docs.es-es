---
title: '&lt;typeindex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <typeindex>
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
ms.openlocfilehash: e22ce63c01185112ed512217156470e6f2948cd5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278922"
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
