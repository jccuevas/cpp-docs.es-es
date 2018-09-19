---
title: Inicio y terminación de un programa de C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f781df914384b553c53e5c42fe16d4c74c9ef99d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845120"
---
# <a name="c-program-startup-and-termination"></a>Inicio y terminación de un programa de C++

Un programa de C++ realiza las mismas operaciones que un programa de C al inicio del programa y en la finalización del programa, además de algunas más que se describen aquí.

Antes de que el entorno de destino llame a la función `main`, y después de que almacene cualquier valor inicial constante que especifique en todos los objetos que tienen duración estática, el programa ejecuta los constructores restantes de esos objetos estáticos. No se especifica el orden de ejecución entre unidades de traducción, pero puede suponer que algunos objetos [iostreams](../standard-library/iostreams-conventions.md) se inicializan correctamente para que los usen estos constructores estáticos. Estos flujos de texto de control son:

- [cin](../standard-library/iostream.md#cin): para la entrada estándar.

- [cout](../standard-library/iostream.md#cout): para la salida estándar.

- [cerr](../standard-library/iostream.md#cerr): para la salida de error estándar no almacenado en el búfer.

- [clog](../standard-library/iostream.md#clog): para la salida de error estándar almacenado en el búfer.

También puede usar estos objetos dentro de los destructores a los que llaman los objetos estáticos, durante la finalización del programa.

Al igual que con C, al volver de `main` o llamar a `exit`, se llama a todas las funciones registradas con `atexit` en orden inverso de registro. Una excepción producida a partir de una función registrada de ese tipo llama a `terminate`.

## <a name="see-also"></a>Vea también

[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
