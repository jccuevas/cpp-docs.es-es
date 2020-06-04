---
title: Inicio y terminación de un programa de C++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
ms.openlocfilehash: e59e8852172a998e4bf4f42f9f919dc29c2ded85
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450653"
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

[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
