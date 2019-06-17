---
title: Propiedades del depurador (C++ para Linux) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
ms.openlocfilehash: d76e398d648db7c5cf65e4ca2bb1665aef4359ad
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821402"
---
# <a name="c-debugging-properties-linux-c"></a>Propiedades de depuración de C++ (C++ para Linux)

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

Propiedad. | Descripción | Opciones
--- | ---| ---
Equipo de depuración remoto | **Visual Studio 2019 versión 16.1**: Especifica el equipo donde se va a depurar el programa. Puede ser diferente del equipo de compilación remoto especificado en la página [General](general-linux.md).
Comando anterior al inicio | Comando que se ejecuta en el shell antes de que el depurador se inicie, y que se puede usar para modificar el entorno de depuración.
Programa | Ruta de acceso completa en el equipo remoto al programa que se va a depurar. Si se deja en blanco o sin modificar, el valor predeterminado es la salida del proyecto actual.
Argumentos de programa | Argumentos de la línea de comandos que deben pasarse al programa que se va a depurar.
Directorio de trabajo | Directorio de trabajo de la aplicación remota. De forma predeterminada, es el directorio principal de usuario.
Comandos adicionales del depurador | Comandos `gdb` adicionales para que los ejecute el depurador antes de iniciar la depuración.
Número de puerto del depurador | Número de puerto para la comunicación del depurador con el depurador remoto. El puerto no debe estar usándose en el sistema local. Este valor debe ser positivo y estar comprendido entre 1 y 65 535. Si no se proporciona, se usa un número de puerto que esté libre.
Número de puerto del depurador remoto | Número de puerto en el que está escuchando el servidor del depurador remoto `gdbserver` en el sistema remoto. El puerto debe estar libre en el sistema remoto. Este valor debe ser positivo y estar comprendido entre 1 y 65 535. Si no se proporciona, se usa un número de puerto libre a partir de 4444.
Modo de depuración | Especifica la manera en que el depurador se interrelaciona con `gdb`. En el *modo gdb*, el depurador controla `gdb` a través del shell en el sistema remoto. En el *modo gdbserver*, `gdb` se ejecuta en modo local y se conecta al `gdbserver` que se ejecuta en el sistema remoto. | **gdbserver**<br/>**gdb**
Rutas de búsqueda de símbolos adicionales | Ruta de búsqueda adicional para símbolos de depuración (solib-search-path).
Depurar procesos secundarios | Especifica si se habilita la depuración de procesos secundarios.
Habilitar impresión con sangría de Python | Habilite la impresión con sangría de los valores de expresión. Solo se admite en el modo de depuración gdb.
Archivo de visualización | Archivo de visualización nativo predeterminado (.natvis) que contiene directivas de visualización para los tipos SLT. Otros archivos .natvis que pertenecen a la solución actual se cargan automáticamente.
Asignación de ruta de acceso de archivo para orígenes adicionales | Equivalencias de ruta de acceso adicionales para que use el depurador a fin de asignar nombres de archivo de origen de Windows a nombres de archivo de origen de Linux. El formato es "\<windows-path> =\<linux-path>;...". Se hace referencia a un nombre de archivo de origen encontrado en la ruta de acceso de Windows como si se encontrara en la misma posición relativa en la ruta de acceso de Linux. Los archivos encontrados en el proyecto local no requieren ninguna asignación adicional.

::: moniker-end
