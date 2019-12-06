---
title: Personalizar el procesamiento de línea de comandos de C++
ms.date: 11/04/2016
f1_keywords:
- _setenvp
- _setargv
helpviewer_keywords:
- command line [C++], processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line [C++], processing arguments
- suppressing environment processing
- _setenvp function
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
ms.openlocfilehash: 1541840521695658b5c4d809ba7e11767b1330a2
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857559"
---
# <a name="customizing-c-command-line-processing"></a>Personalizar el procesamiento de línea de comandos de C++

**Específicos de Microsoft**

Si el programa no acepta argumentos de línea de comandos, puede guardar una pequeña cantidad de espacio suprimiendo el uso de la rutina de biblioteca que realiza el procesamiento de la línea de comandos. Esta rutina se denomina `_setargv` y se describe en [expansión de caracteres comodín](../cpp/wildcard-expansion.md). Para suprimir su uso, defina una rutina que no hace nada en el archivo que contiene la función `main` y asígnele el nombre `_setargv`. A continuación, la definición de `_setargv`satisface la llamada a `_setargv` y no se carga la versión de la biblioteca.

Del mismo modo, si nunca tiene acceso a la tabla de entorno mediante el argumento `envp`, puede proporcionar su propia rutina vacía para usar en lugar de `_setenvp`, la rutina de procesamiento de entorno. Al igual que con la función `_setargv`, `_setenvp` se debe declarar como **extern "C"** .

El programa puede realizar llamadas a la familia de rutinas `spawn` o `exec` en la biblioteca en tiempo de ejecución de C. Si es así, no debe suprimir la rutina de procesamiento de entorno, puesto que esta rutina se utiliza para pasar un entorno del proceso primario al proceso secundario.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[main: Inicio de programa](../cpp/main-program-startup.md)