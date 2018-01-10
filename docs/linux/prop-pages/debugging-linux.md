---
title: Propiedades del depurador (C++ para Linux) | Microsoft Docs
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 11ebb11cca19c98bf9f72b9f99f33d66464cd485
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="c-debugging-properties-linux-c"></a>Propiedades de depuración de C++ (C++ para Linux)

Property | Description | Opciones
--- | ---| ---
Comando anterior al inicio | Comando que se ejecuta en el shell antes de que se inicie la depuración y antes de que se ejecute el depurador. Se puede usar para modificar el entorno de depuración.
Programa | Ruta de acceso completa al programa que se va a depurar en el sistema remoto. Es una ruta de acceso del sistema remoto. Si deja en blanco o sin modificar, el valor predeterminado es la salida del proyecto actual.
Argumentos de programa | Argumentos de la línea de comandos que deben pasarse al programa que se va a depurar.
Directorio de trabajo | Directorio de trabajo de la aplicación remota. De forma predeterminada, es el directorio principal de usuario.
Comandos adicionales del depurador | Comandos gdb adicionales para que los ejecute el depurador antes de iniciar la depuración.
Número de puerto del depurador | Número de puerto para la comunicación del depurador con el depurador remoto. El puerto no debe estar usándose en el sistema local. Este valor debe ser positivo y estar comprendido entre 1 y 65535. Si no se proporciona, se usará un número de puerto que esté libre.
Número de puerto del depurador remoto | Número de puerto en el que está escuchando el servidor del depurador remoto (gdbserver) en el sistema remoto. El puerto debe estar libre en el sistema remoto. Este valor debe ser positivo y estar comprendido entre 1 y 65535. Si no se proporciona, se usará un número de puerto libre a partir de 4444.
Modo de depuración | Especifica la manera en que el depurador se interrelaciona con gdb. En el modo gdb, el depurador controla gdb a través del shell en el sistema remoto. En el modo gdbserver, gdb se ejecuta en modo local y se conecta al gdbserver que se ejecuta en el sistema remoto. | **gdbserver**<br>**gdb**<br>
Rutas de búsqueda de símbolos adicionales | Ruta de búsqueda adicional para símbolos de depuración (solib-search-path).
Depurar procesos secundarios | Especifica si se habilita la depuración de procesos secundarios.
Habilitar impresión con sangría de Python | Habilite la impresión con sangría de los valores de expresión. Solo se admite en el modo de depuración gdb.
Archivo de visualización | Archivo de visualización nativo predeterminado (.natvis) que contiene directivas de visualización para los tipos SLT. Otros archivos .natvis que pertenecen a la solución actual se cargarán automáticamente.
Asignación de ruta de acceso de archivo para orígenes adicionales | Equivalencias de ruta de acceso adicionales para que use el depurador a fin de asignar nombres de archivo de origen de Windows a nombres de archivo de origen de Linux. El formato es "\<windows-path> =\<linux-path>;...". Se hará referencia a un nombre de archivo de origen encontrado en la ruta de acceso de Windows como si se hubiera encontrado en la misma posición relativa en la ruta de acceso de Linux. Los archivos encontrados en el proyecto local no requieren ninguna asignación adicional.
