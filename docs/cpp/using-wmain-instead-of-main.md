---
title: "Usar wmain en vez de main | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "wmain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "main (función), frente a wmain"
  - "wmain (función)"
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar wmain en vez de main
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 En el modelo de programación de Unicode, puede definir una versión con caracteres anchos de la función **main**.  Utilice **wmain** en lugar de **main** si desea escribir código portable conforme con la especificación Unicode.  
  
 Se pueden declarar parámetros formales a **wmain** utilizando un formato similar a **main**.  A continuación, se pueden pasar al programa argumentos de caracteres anchos y, opcionalmente, un puntero a entorno de caracteres anchos.  Los parámetros `argv` y `envp` de **wmain** son del tipo `wchar_t*`.  
  
 Si el programa utiliza una función **main**, el entorno de caracteres multibyte lo crea el sistema operativo durante el inicio del programa.  Se crea una copia de caracteres anchos del entorno solo si es necesario \(por ejemplo, por una llamada a las funciones [\_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md) o [\_wputenv](../c-runtime-library/reference/putenv-wputenv.md)\).  En la primera llamada a `_wputenv`, o en la primera llamada a `_wgetenv` si ya existe un entorno MBCS, se crea un entorno correspondiente de cadena de caracteres anchos, y la variable global `_wenviron`, que es una versión con caracteres anchos de la variable global `_environ`, señala a dicho entorno.  En este punto, existen dos copias del entorno \(MBCS y Unicode\) simultáneamente que el sistema operativo mantiene a lo largo de la vida del programa.  
  
 De forma similar, si el programa utiliza una función **wmain**, se crea un entorno MBCS \(ASCII\) en la primera llamada a `_putenv` o `getenv`, y la variable global `_environ` señala a dicho entorno.  
  
 Para obtener más información sobre el entorno MBCS, vea [Juegos de caracteres de un solo byte y multibyte](../c-runtime-library/single-byte-and-multibyte-character-sets.md) en la *Referencia de la biblioteca en tiempo de ejecución.*  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [main: inicio de programa](../cpp/main-program-startup.md)