---
title: message (Pragma)
ms.date: 08/29/2019
f1_keywords:
- message_CPP
- vc-pragma.message
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
ms.openlocfilehash: 48605fbef3b6d81c140e663e950429cd3dcf9b19
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218798"
---
# <a name="message-pragma"></a>message (Pragma)

Envía un literal de cadena al resultado estándar sin finalizar la compilación.

## <a name="syntax"></a>Sintaxis

> **mensaje de #pragma (** *cadena de mensaje* **)**

## <a name="remarks"></a>Comentarios

Un uso típico del pragma **Message** es mostrar mensajes informativos en tiempo de compilación.

El parámetro *de cadena de mensaje* puede ser una macro que se expande a un literal de cadena y puede concatenar estas macros con literales de cadena en cualquier combinación.

Si usa una macro predefinida en el pragma **Message** , la macro debe devolver una cadena. De lo contrario, tendrá que convertir el resultado de la macro en una cadena.

En el fragmento de código siguiente se usa el pragma **Message** para mostrar los mensajes durante la compilación:

```cpp
// pragma_directives_message1.cpp
// compile with: /LD
#if _M_IX86 >= 500
#pragma message("_M_IX86 >= 500")
#endif

#pragma message("")

#pragma message( "Compiling " __FILE__ )
#pragma message( "Last modified on " __TIMESTAMP__ )

#pragma message("")

// with line number
#define STRING2(x) #x
#define STRING(x) STRING2(x)

#pragma message (__FILE__ "[" STRING(__LINE__) "]: test")

#pragma message("")
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
