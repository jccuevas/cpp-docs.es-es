---
title: mensaje | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- message_CPP
- vc-pragma.message
dev_langs:
- C++
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3ce9091fe380f7d255dd321dbb9eb5ca7134b8d
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538901"
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