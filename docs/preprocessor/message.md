---
title: mensaje | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- message_CPP
- vc-pragma.message
dev_langs: C++
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad91fdc0fb024fe87c2096f91962f715c0835262
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
 Si utiliza una macro predefinida en el **mensaje** pragma, la macro debe devolver una cadena, la persona tendrá que convertir el resultado de la macro en una cadena.  
  
 En el fragmento de código siguiente se utiliza la **mensaje** pragma para mostrar mensajes durante la compilación:  
  
```  
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