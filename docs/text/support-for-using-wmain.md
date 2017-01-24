---
title: "Compatibilidad con el uso de wmain | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "wWinMain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "caracteres anchos [C++], wmain (función)"
  - "wmain (función)"
  - "wWinMain (función)"
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
caps.latest.revision: 9
caps.handback.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Compatibilidad con el uso de wmain
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ admite la definición de una función **wmain** y el paso de argumentos de caracteres anchos a una aplicación Unicode.  Se pueden declarar parámetros formales a **wmain** utilizando un formato similar a **main**.  A continuación, se pueden pasar al programa argumentos de caracteres anchos y, opcionalmente, un puntero a entorno de caracteres anchos.  Los parámetros `argv` y `envp` de **wmain** son del tipo `wchar_t*`.  Por ejemplo:  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
> [!NOTE]
>  Las aplicaciones de Unicode MFC utilizan **wWinMain** como punto de entrada.  En este caso, `CWinApp::m_lpCmdLine` es una cadena de Unicode.  Asegúrese de establecer **wWinMainCRTStartup** con la opción de vinculador [\/ENTRY](../build/reference/entry-entry-point-symbol.md).  
  
 Si el programa utiliza una función **main**, el entorno de caracteres multibyte lo crea la biblioteca en tiempo de ejecución durante el inicio del programa.  Se crea una copia de caracteres anchos del entorno sólo si es necesario \(por ejemplo, por una llamada a las funciones `_wgetenv` o `_wputenv`\).  En la primera llamada a `_wputenv`, o en la primera llamada a `_wgetenv`, si ya existe un entorno MBCS, se crea un entorno correspondiente de cadena de caracteres anchos.  Posteriormente, la variable global `_wenviron`, que es una versión con caracteres anchos de la variable global `_environ`, apunta al entorno.  En este punto, existen dos copias del entorno \(MBCS y Unicode\) simultáneamente que son mantenidas por el sistema en tiempo de ejecución a lo largo de la vida del programa.  
  
 De forma similar, si el programa utiliza una función **wmain**, se crea un entorno de caracteres anchos durante el inicio del programa y la variable global `_wenviron` apunta a dicho entorno.  En la primera llamada a `_putenv` o `getenv` se crea un entorno MBCS \(ASCII\) y la variable global `_environ` apunta a dicho entorno.  
  
## Vea también  
 [Compatibilidad con Unicode](../text/support-for-unicode.md)   
 [Resumen de la programación con Unicode](../text/unicode-programming-summary.md)   
 [WinMain \(Función\)](http://msdn.microsoft.com/library/windows/desktop/ms633559)