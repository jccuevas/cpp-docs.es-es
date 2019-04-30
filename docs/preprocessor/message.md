---
title: message
ms.date: 11/04/2016
f1_keywords:
- message_CPP
- vc-pragma.message
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
ms.openlocfilehash: e9383238fd308ec59a9767f56af1c07fc3cfcf07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371744"
---
# <a name="message"></a>message
Envía un literal de cadena al resultado estándar sin finalizar la compilación.

## <a name="syntax"></a>Sintaxis

```
#pragma message( messagestring )
```

## <a name="remarks"></a>Comentarios

Un uso típico de la **mensaje** pragma consiste en Mostrar mensajes informativos en tiempo de compilación.

El *messagestring* parámetro puede ser una macro que se expande a un literal de cadena y puede concatenar estas macros con literales de cadena en cualquier combinación.

Si utiliza una macro predefinida en el **mensaje** pragma, la macro debe devolver una cadena, de lo contrario, tendrá que convertir el resultado de la macro en una cadena.

El siguiente fragmento de código utiliza el **mensaje** pragma para mostrar mensajes durante la compilación:

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

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)