---
title: "main: inicio de programa | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc.main.startup"
  - "_tmain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tmain (función)"
  - "puntos de entrada, programa"
  - "main (función), inicio de programa"
  - "inicio de programa [C++]"
  - "código de inicio, main (función)"
  - "wmain (función)"
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# main: inicio de programa
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una función especial denominada `main` es el punto inicial de ejecución para todos los programas de C y [!INCLUDE[TLA#tla_cpp](../cpp/includes/tlasharptla_cpp_md.md)].  Si escribe código que cumple el modelo de programación de [!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)], puede utilizar `wmain`, que es la versión con caracteres anchos de `main`.  
  
 El compilador no predefine la función `main`.  Debe proporcionarse en el texto del programa.  
  
 La sintaxis de declaración de `main` es  
  
```  
int main();  
```  
  
 u opcionalmente  
  
```  
int main(int argc, char *argv[], char *envp[]);  
```  
  
## Específicos de Microsoft  
 La sintaxis de declaración de `wmain` es la siguiente:  
  
```  
int wmain( );  
```  
  
 u opcionalmente  
  
```  
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 También puede utilizar `_tmain`, que se define en TCHAR.h.  `_tmain` se resuelve en `main` a menos que se defina \_UNICODE.  En ese caso, `_tmain` se resuelve en `wmain`.  
  
 De forma alternativa, se pueden declarar que las funciones `main` y `wmain` devuelvan `void` \(ningún valor devuelto\).  Si declara que `main` o `wmain` devuelvan `void`, no se puede devolver un código de salida al proceso primario o al sistema operativo mediante una instrucción [return](../cpp/return-statement-in-program-termination-cpp.md).  Para devolver un código de salida cuando `main` o `wmain` se declaran como `void`, debe utilizar la función [exit](../cpp/exit-function.md).  
  
## FIN de Específicos de Microsoft  
 El lenguaje define los tipos `argc` y `argv`.  Los nombres `argc`, `argv` y `envp` son tradicionales, pero no los requiere el compilador.  Para obtener más información y un ejemplo, vea [Definiciones de argumentos](../cpp/argument-definitions.md).  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Usar wmain en vez de main](../cpp/using-wmain-instead-of-main.md)   
 [Restricciones de la función main](../cpp/main-function-restrictions.md)