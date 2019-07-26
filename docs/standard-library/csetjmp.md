---
title: '&lt;csetjmp&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csetjmp>
helpviewer_keywords:
- csetjmp header
ms.assetid: 8f21fddd-5e9b-4219-a848-581cdd3569d9
ms.openlocfilehash: 8f3a1a622776d5dd2ef3d22aaa3436933c5a7137
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452398"
---
# <a name="ltcsetjmpgt"></a>&lt;csetjmp&gt;

Incluye el encabezado \<setjmp.h> de la biblioteca estándar de C y agrega los nombres asociados al espacio de nombres `std`.

## <a name="syntax"></a>Sintaxis

```cpp
#include <csetjmp>

using jmp_buf = see below;
```

## <a name="functions"></a>Funciones

```cpp
[[noreturn]] void longjmp(jmp_buf env, int val);
```

## <a name="macros"></a>Macros

```cpp
#define setjmp(env)
```

## <a name="remarks"></a>Comentarios

Incluir este encabezado también garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar de C se declaran en el espacio de nombres `std`.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
