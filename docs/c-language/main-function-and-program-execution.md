---
title: Función main y ejecución del programa
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
ms.openlocfilehash: e975f09b62ffbb536790c13eb8614453b1c1e8b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610436"
---
# <a name="main-function-and-program-execution"></a>Función main y ejecución del programa

Cada programa de C tiene una función principal que se debe llamar **main**. Si su código sigue el modelo de programación Unicode, puede utilizar la versión de carácter ancho de **main**, **wmain**. La función **main** sirve como punto de partida para la ejecución del programa. Normalmente, controla la ejecución del programa dirigiendo las llamadas a otras funciones del programa. Un programa deja de ejecutarse normalmente al final de **main**, aunque puede finalizar en otros puntos del programa por distintos motivos. A veces, quizás cuando se detecta un error, puede resultar conveniente forzar la finalización de un programa. Para ello, utilice la función **exit**. Vea la *Referencia de la biblioteca en tiempo de ejecución* para obtener información y un ejemplo sobre cómo usar la función [exit](../c-runtime-library/reference/exit-exit-exit.md).

## <a name="syntax"></a>Sintaxis

```
main( int argc, char *argv[ ], char *envp[ ] )
```

## <a name="remarks"></a>Comentarios

Las funciones incluidas en el programa de origen realizan una o más tareas concretas. La función **main** puede llamar a estas funciones para que realicen sus respectivas tareas. Cuando **main** llama a otra función, pasa el control de la ejecución a la función, de modo que la ejecución comienza en la primera instrucción de la función. Una función devuelve el control a **main** cuando se ejecuta una instrucción `return` o cuando se llega al final de la función.

Puede declarar cualquier función, incluida **main**, para que tenga parámetros. El término “parámetro” o “parámetro formal” hace referencia al identificador que recibe un valor pasado a una función. Vea [Parámetros](../c-language/parameters.md) para obtener información sobre cómo pasar argumentos a parámetros. Cuando una función llama a otra, la función a la que se llama recibe los valores de sus parámetros de la función que realiza la llamada. Estos valores se denominan “argumentos”. Puede declarar parámetros formales para **main** para que pueda recibir argumentos de la línea de comandos con este formato:

Si desea pasar información a la función **main**, los parámetros se denominan tradicionalmente `argc` y `argv`, aunque el compilador de C no obliga a usar estos nombres. Los tipos de `argc` y `argv` los define el lenguaje C. Tradicionalmente, si se pasa un tercer parámetro a **main**, ese parámetro se denomina `envp`. Los ejemplos incluidos más adelante en esta sección muestran cómo utilizar estos tres parámetros para acceder a los argumentos de la línea de comandos. En las siguientes secciones se explican estos parámetros.

Vea [Usar wmain](../c-language/using-wmain.md) para obtener una descripción de la versión de carácter ancho de **main**.

## <a name="see-also"></a>Vea también

[main: Inicio de programa](../cpp/main-program-startup.md)<br/>
[Analizar los argumentos de la línea de comandos de C](../c-language/parsing-c-command-line-arguments.md)
