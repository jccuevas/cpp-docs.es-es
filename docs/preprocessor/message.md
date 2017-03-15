---
title: "message | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "message_CPP"
  - "vc-pragma.message"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "message (pragma)"
  - "pragma (directivas), message"
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# message
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Envía un literal de cadena al resultado estándar sin finalizar la compilación.  
  
## Sintaxis  
  
```  
  
#pragma message( messagestring )  
```  
  
## Comentarios  
 Un uso típico de la instrucción pragma **message** es mostrar mensajes informativos en tiempo de compilación.  
  
 El parámetro *messagestring* puede ser una macro que se expanda a un literal de cadena, y puede concatenar estas macros con literales de cadena en cualquier combinación.  
  
 Si utiliza una macro predefinida en la instrucción pragma **message**, la macro debe devolver una cadena; en caso contrario, tendrá que convertir el resultado de la macro en una cadena.  
  
 En el fragmento de código siguiente se utiliza la instrucción pragma **message** para mostrar mensajes durante la compilación:  
  
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
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)