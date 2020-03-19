---
title: Propiedades del depuradorC++de Android ()
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 3ac896b384181e4e2b436368f39a343d35fe321a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79470278"
---
# <a name="android-debugger-properties"></a>Propiedades del depurador de Android

| Propiedad | Descripción | Opciones |
|--|--|--|
| Tipo de depurador | Especifica qué tipo de código se va a depurar. | **Solo nativo**<br /><br />**Solo Java** |
| Destino de depuración | Especifica el emulador o dispositivo que se usará para la depuración. Si no se está ejecutando ningún emulador, use "Android Virtual Device (AVD) Manager" para iniciar un dispositivo. |
| Paquete que se iniciará | Especifica la ubicación del archivo *.apk* que se va a depurar. Esta opción inicia el paquete (APK) cuando se depura la aplicación. |
| Actividad de inicio | La actividad de Android que se usará para iniciar la aplicación tiene que coincidir con la que se usa en el manifiesto. Presione Aplicar para recuperar la lista de *AndroidManifest.xml* y rellenarla de forma dinámica. |
| Rutas de búsqueda de símbolos adicionales | Ruta de búsqueda adicional para los símbolos de depuración. |
| Rutas de búsqueda de código fuente Java adicionales | Rutas de búsqueda adicional para los archivos de código fuente Java. Solo se aplica cuando el tipo de depurador es únicamente Java. |
