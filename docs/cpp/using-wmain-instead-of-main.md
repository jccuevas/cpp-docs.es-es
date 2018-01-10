---
title: Usar wmain en vez de main | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: wmain
dev_langs: C++
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d43ab12c42315d735220af8f91c40d8b6a5cc4f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-wmain-instead-of-main"></a>Usar wmain en vez de main
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 En el modelo de programación de Unicode, puede definir una versión con caracteres anchos de la función **main**. Use **wmain** en lugar de **principal** si desea escribir código portable conforme con la especificación Unicode.  
  
 Se pueden declarar parámetros formales para **wmain** utilizando un formato similar a **main**. A continuación, se pueden pasar al programa argumentos de caracteres anchos y, opcionalmente, un puntero a entorno de caracteres anchos. Los parámetros `argv` y `envp` de **wmain** son del tipo `wchar_t*`.  
  
 Si el programa utiliza una **principal** función, el entorno de caracteres multibyte lo crea el sistema operativo al inicio del programa. Se crea una copia de caracteres anchos del entorno sólo si es necesario (por ejemplo, mediante una llamada a la [_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md) o [_wputenv](../c-runtime-library/reference/putenv-wputenv.md) funciones). En la primera llamada a `_wputenv`, o en la primera llamada a `_wgetenv` si ya existe un entorno MBCS, se crea un entorno correspondiente de cadena de caracteres anchos, y la variable global `_wenviron`, que es una versión con caracteres anchos de la variable global `_environ`, señala a dicho entorno. En este punto, existen dos copias del entorno (MBCS y Unicode) simultáneamente que el sistema operativo mantiene a lo largo de la vida del programa.  
  
 De forma similar, si el programa utiliza una **wmain** función, se crea un entorno MBCS (ASCII) en la primera llamada a `_putenv` o `getenv`y apunta a la `_environ` (variable global).  
  
 Para obtener más información sobre el entorno MBCS, vea [un solo byte y juegos de caracteres Multibyte](../c-runtime-library/single-byte-and-multibyte-character-sets.md) en el *referencia de la biblioteca de tiempo de ejecución.*  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [main: Inicio de programa](../cpp/main-program-startup.md)