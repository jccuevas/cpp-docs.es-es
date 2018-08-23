---
title: 'Main: inicio del programa | Microsoft Docs'
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
ms.openlocfilehash: 824bb7059e13c76af0c2f739676d32afc04aa0c7
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42571718"
---
# <a name="main-program-startup"></a>main: inicio de programa
Una función especial denominada **principal** es el punto inicial de la ejecución de todos los programas de C y C++. Si está escribiendo código que se adhiera al modelo de programación Unicode, puede usar `wmain`, que es la versión de caracteres anchos de **principal**.  
  
 El **principal** el compilador no predefine la función. Debe proporcionarse en el texto del programa.  
  
 La sintaxis de declaración de **principal** es  
  
```cpp 
int main();  
```  
  
 u opcionalmente  
  
```cpp 
int main(int argc, char *argv[], char *envp[]);  
```  
  
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 La sintaxis de declaración de `wmain` es la siguiente:  
  
```cpp 
int wmain( );  
```  
  
 u opcionalmente  
  
```cpp 
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 También puede utilizar `_tmain`, que se define en TCHAR.h. `_tmain` se resuelve como **principal** a menos que se define _UNICODE. En ese caso, `_tmain` se resuelve en `wmain`.  
  
 Como alternativa, el **principal** y `wmain` funciones se pueden declarar como devolver **void** (ningún valor devuelto). Si declara **principal** o `wmain` que devuelva **void**, no se puede devolver un código de salida para el sistema operativo o el proceso primario mediante un [devolver](../cpp/return-statement-in-program-termination-cpp.md) instrucción. Para devolver una código de salida cuando **principal** o `wmain` se declara como **void**, debe usar el [salir](../cpp/exit-function.md) función.  
  
**FIN de Específicos de Microsoft**  
 El lenguaje define los tipos `argc` y `argv`. Los nombres `argc`, `argv` y `envp` son tradicionales, pero no los requiere el compilador. Para obtener más información y un ejemplo, vea [definiciones de argumentos](../cpp/argument-definitions.md).  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Usar wmain en vez de main](../cpp/using-wmain-instead-of-main.md)   
 [Restricciones de la función Main](../cpp/main-function-restrictions.md)   
 [Analizar los argumentos de la línea de comandos de C++](../cpp/parsing-cpp-command-line-arguments.md)