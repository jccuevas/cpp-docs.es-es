---
title: Propiedades generales (proyecto de C++ para Linux) | Microsoft Docs
ms.date: 9/26/2017
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: bc4eb39d2d735f8f7f782d2827bf2b938c5c2457
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461339"
---
# <a name="general-properties-linux-c"></a>Propiedades generales (C++ para Linux)

Propiedad. | Descripción | Opciones
--- | ---| ---
Directorio de salida | Especifica una ruta de acceso relativa al directorio de archivos de salida; puede incluir variables de entorno.
Directorio intermedio | Especifica una ruta de acceso relativa al directorio de archivos intermedios; puede incluir variables de entorno.
Nombre de destino | Especifica el nombre del archivo que generará el proyecto.
Extensión de destino | Especifica una extensión de archivo que generará este proyecto. (Ejemplo: .a)
Extensiones para eliminar al limpiar | Especificación de comodines delimitados por punto y coma para indicar qué archivos del directorio de archivos intermedios se deben eliminar al limpiar o recompilar.
Archivo de registro de compilación | Especifica el archivo de registro de compilación en el que se escribe cuando está habilitada la opción de registro de compilación.
Conjunto de herramientas de la plataforma | Especifica el conjunto de herramientas usado para compilar la configuración actual. Si no se establece, se usa el conjunto de herramientas predeterminado.
Máquina de compilación remota | Máquina o dispositivo de destino que debe usarse para la compilación, implementación y depuración remotas.
Directorio raíz de la compilación remota | Especifica una ruta de acceso a un directorio de la máquina o el dispositivo remotos.
Directorio del proyecto de compilación remota | Especifica una ruta de acceso a un directorio de la máquina o el dispositivo remotos para el proyecto.
Tipo de configuración | Especifica el tipo de salida que genera esta configuración. | **Biblioteca dinámica (.so)**: biblioteca dinámica (.so)<br>**Biblioteca estática (.a)**: biblioteca estática (.a)<br>**Aplicación (.out)**: aplicación (.out)<br>**Archivo Make**: archivo Make<br>
Uso de STL | Especifica la biblioteca estándar de C++ que se usará para esta configuración. | **Standard C++ Library para GNU compartida**<br>**Standard C++ Library para GNU estática (-static)**<br>
