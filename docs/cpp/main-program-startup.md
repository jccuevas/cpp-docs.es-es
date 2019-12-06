---
title: 'main: inicio de programa'
ms.date: 11/04/2016
f1_keywords:
- vc.main.startup
- _tmain
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
ms.openlocfilehash: 29e1b77c2e36c66e4e6fc4ec30a73af4d57654a0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857442"
---
# <a name="main-program-startup"></a>main: inicio de programa

Una función especial denominada **Main** es el punto de inicio de la ejecución de todos C++ los programas de C y. Si está escribiendo código que se ajusta al modelo de programación Unicode, puede utilizar `wmain`, que es la versión con caracteres anchos de **Main**.

La función **Main** no está predefinida por el compilador. Debe proporcionarse en el texto del programa.

La sintaxis de declaración para **Main** es

```cpp
int main();
```

u opcionalmente

```cpp
int main(int argc, char *argv[], char *envp[]);
```

**Específicos de Microsoft**

La sintaxis de declaración de `wmain` es la siguiente:

```cpp
int wmain( );
```

u opcionalmente

```cpp
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

También puede usar `_tmain`, que se define en TCHAR. h. `_tmain` se resuelve en **Main** a menos que se defina _UNICODE. En ese caso, `_tmain` se resuelve en `wmain`.

Como alternativa, las funciones **Main** y `wmain` se pueden declarar como si devolvieran **void** (ningún valor devuelto). Si declara **Main** o `wmain` como si devolviera **void**, no puede devolver un código de salida al proceso primario o al sistema operativo mediante una instrucción [Return](../cpp/return-statement-in-program-termination-cpp.md) . Para devolver un código de salida cuando **Main** o `wmain` se declara como **void**, debe usar la función [Exit](../cpp/exit-function.md) .

**FIN de Específicos de Microsoft**

El lenguaje define los tipos `argc` y `argv`. Los nombres `argc`, `argv` y `envp` son tradicionales, pero no los requiere el compilador. Para obtener más información y un ejemplo, vea [definiciones de argumentos](../cpp/argument-definitions.md).

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Usar wmain en vez de main](../cpp/using-wmain-instead-of-main.md)<br/>
[Restricciones de la función main](../cpp/main-function-restrictions.md)<br/>
[Analizar los argumentos de la línea de comandos de C++](../cpp/parsing-cpp-command-line-arguments.md)
