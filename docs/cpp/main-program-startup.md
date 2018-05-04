---
title: 'Main: inicio del programa | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- vc.main.startup
- _tmain
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2999596fe30afca4c9945efc34a8537e9f45e14a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="main-program-startup"></a>main: inicio de programa
Una función especial denominada `main` es el punto inicial de ejecución para todos los programas de C y C++. Si escribe código que cumple el modelo de programación de [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)], puede utilizar `wmain`, que es la versión con caracteres anchos de `main`.  
  
 El compilador no predefine la función `main`. Debe proporcionarse en el texto del programa.  
  
 La sintaxis de declaración de `main` es  
  
```  
int main();  
```  
  
 u opcionalmente  
  
```  
int main(int argc, char *argv[], char *envp[]);  
```  
  
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 La sintaxis de declaración de `wmain` es la siguiente:  
  
```  
int wmain( );  
```  
  
 u opcionalmente  
  
```  
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 También puede utilizar `_tmain`, que se define en TCHAR.h. `_tmain` se resuelve en `main` a menos que se defina _UNICODE. En ese caso, `_tmain` se resuelve en `wmain`.  
  
 De forma alternativa, se pueden declarar que las funciones `main` y `wmain` devuelvan `void` (ningún valor devuelto). Si declara `main` o `wmain` como devolver `void`, no se puede devolver un código de salida al proceso primario o al sistema operativo mediante un [devolver](../cpp/return-statement-in-program-termination-cpp.md) instrucción. Para devolver una código de salida cuando `main` o `wmain` se declara como `void`, debe utilizar el [salir](../cpp/exit-function.md) función.  
  
**FIN de Específicos de Microsoft**  
 El lenguaje define los tipos `argc` y `argv`. Los nombres `argc`, `argv` y `envp` son tradicionales, pero no los requiere el compilador. Para obtener más información y un ejemplo, vea [definiciones de argumentos](../cpp/argument-definitions.md).  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Usar wmain en vez de main](../cpp/using-wmain-instead-of-main.md)   
 [Restricciones de la función main](../cpp/main-function-restrictions.md)