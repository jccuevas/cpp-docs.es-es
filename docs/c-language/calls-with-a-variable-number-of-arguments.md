---
title: "Llamadas con un número variable de argumentos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- arguments [C++], variable number of
- VARARGS.H
- ellipses (...), variable number of arguments
- STDARGS.H
- function calls, arguments
- '... ellipsis'
- function calls, variable number of arguments
ms.assetid: 8808fb26-4822-42f5-aba3-ac64b54e151b
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 8b6b922ecbbeafe1f97025861ae9e8b933a9226c
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="calls-with-a-variable-number-of-arguments"></a>Llamadas con un número variable de argumentos
Una lista parcial de parámetros puede finalizarse con la notación de puntos suspensivos, una coma seguida de tres puntos (**, ...**), para indicar que puede que se hayan pasado más argumentos a la función, pero no se proporciona más información sobre ellos. La comprobación de tipos no se realiza en esos argumentos. Al menos un parámetro debe preceder a la notación de puntos suspensivos y la notación de puntos suspensivos debe ser el último token de la lista de parámetros. Sin la notación de puntos suspensivos, el comportamiento de una función es indefinido si recibe parámetros adicionales a los declarados en la lista de parámetros.  
  
 Para llamar a una función con un número variable de argumentos, solo hay que especificar un número de argumentos en la llamada de función. Un ejemplo es la función `printf` de la biblioteca en tiempo de ejecución de C. La llamada de función debe incluir un argumento para cada nombre de tipo declarado en la lista de parámetros o la lista de tipos de argumento.  
  
 Todos los argumentos especificados en la llamada de función se colocan en la pila, a menos que se especifique la convención de llamada `__fastcall`. El número de parámetros declarados para la función determina cuántos argumentos se toman de la pila y se asignan a los parámetros. El usuario es responsable de recuperar los argumentos adicionales de la pila y determinar cuántos argumentos están presentes. El archivo STDARG.H contiene macros de estilo ANSI para el acceso a los argumentos de funciones que toman un número variable de argumentos. Además, se siguen admitiendo las macros de estilo XENIX en VARARGS.H.  
  
 Esta declaración de ejemplo es para una función que llama a un número variable de argumentos:  
  
```  
int average( int first, ...);  
```  
  
## <a name="see-also"></a>Vea también  
 [Llamadas de función](../c-language/function-calls.md)
