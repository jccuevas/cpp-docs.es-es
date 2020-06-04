---
title: Propiedades del depurador de Android (C++)
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 23fd871f030593607cf374870b96e09d8bc2da7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374200"
---
# <a name="android-debugger-properties"></a>Propiedades del depurador de Android

| Propiedad | Descripción | Opciones |
|--|--|--|
| Tipo de depurador | Especifica qué tipo de código se va a depurar. | **Solo para nativos**<br /><br />**Solo Java** |
| Destino de depuración | Especifica el emulador o dispositivo que se usará para la depuración. Si no se está ejecutando ningún emulador, utilice 'Administrador de dispositivos virtuales Android (AVD)' para iniciar un dispositivo. |
| Paquete que se iniciará | Especifica la ubicación del *archivo .apk* que se depurará. Esta opción inicia el paquete (APK) cuando se depura la aplicación. |
| Actividad de inicio | La actividad de Android que se usará para iniciar la aplicación tiene que coincidir con la que se usa en el manifiesto. Presione Aplicar para recuperar la lista de *AndroidManifest.xml* y rellenarla dinámicamente. |
| Rutas de búsqueda de símbolos adicionales | Ruta de búsqueda adicional para los símbolos de depuración. |
| Rutas de búsqueda de código fuente Java adicionales | Rutas de búsqueda adicional para los archivos de código fuente Java. Solo se aplica cuando el tipo de depurador es únicamente Java. |
