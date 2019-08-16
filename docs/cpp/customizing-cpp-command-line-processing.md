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
ms.openlocfilehash: da1b3bdd6392b144f9315add4c19de14c1d14d41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154696"
---
# <a name="customizing-c-command-line-processing"></a>Personalizar el procesamiento de línea de comandos de C++

## <a name="microsoft-specific"></a>Específicos de Microsoft

Si el programa no acepta argumentos de línea de comandos, puede guardar una pequeña cantidad de espacio suprimiendo el uso de la rutina de biblioteca que realiza el procesamiento de la línea de comandos. Esta rutina se denomina `_setargv` y se describe en [expansión de caracteres comodín](../cpp/wildcard-expansion.md). Para suprimir su uso, defina una rutina que no hace nada en el archivo que contiene el `main` funcionando y asígnele el nombre `_setargv`. La llamada a `_setargv` , a continuación, se satisface mediante la definición de `_setargv`, y la versión de la biblioteca no está cargada.

De forma similar, si nunca tiene acceso a la tabla de entorno a través de la `envp` argumento, puede proporcionar una rutina vacía propia que se usará en lugar de `_setenvp`, la rutina de procesamiento de entorno. Al igual que con el `_setargv` función, `_setenvp` debe declararse como **extern "C"**.

El programa puede realizar llamadas a la `spawn` o `exec` familia de rutinas en la biblioteca de tiempo de ejecución de C. Si es así, no debe suprimir la rutina de procesamiento de entorno, puesto que esta rutina se utiliza para pasar un entorno del proceso primario al proceso secundario.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[main: inicio de programa](../cpp/main-program-startup.md)