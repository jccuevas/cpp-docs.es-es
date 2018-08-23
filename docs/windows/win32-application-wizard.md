---
title: Asistente para aplicaciones Win32 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.appwiz.win32.overview
dev_langs:
- C++
helpviewer_keywords:
- Win32 Application Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bdcd101759b35490451bf46bd6e222db469a3fba
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42581247"
---
# <a name="win32-application-wizard"></a>Asistente para aplicaciones Win32

El Asistentes para aplicaciones Win32 de Visual C++ permite crear cuatro tipos de proyecto (que se muestran en los encabezados de la tabla siguiente). En cada caso, puede especificar opciones adicionales apropiadas para el tipo de proyecto que abra. En la tabla siguiente se indican las opciones disponibles para cada tipo de aplicación.

|Tipo de soporte|Aplicación de consola|Aplicación ejecutable (para Windows)|Biblioteca de vínculos dinámicos|Biblioteca estática|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**Proyecto vacío**|Sí|Sí|Sí|No|
|**Exportar símbolos**|No|No|Sí|No|
|**Encabezado precompilado**|No|No|No|Sí|
|**compatibilidad con ATL**|Sí|No|No|No|
|**compatibilidad con MFC**|Sí|No|No|Sí|

## <a name="overview"></a>Información general

En esta página del asistente se describe la configuración del proyecto actual para la aplicación Win32 que se está creando. De forma predeterminada, se establecen las siguientes opciones:

- El proyecto es una aplicación para Windows.

- El proyecto no está vacío.

- El proyecto no contiene símbolos para exportar.

- El proyecto no usa un archivo de encabezado precompilado (esta opción solo está disponible para proyectos de biblioteca estática).

- El proyecto no incluye compatibilidad con MFC ni con ATL.

Para cambiar estos valores predeterminados, haga clic en la pestaña [Configuración de la aplicación](../windows/application-settings-win-32-project-wizard.md) , en la columna izquierda del asistente, y haga los cambios que desee.

Una vez creada una aplicación de escritorio de Windows, puede agregar clases C++ genéricas mediante el Asistente para código [genérico](../ide/generic-cpp-class-wizard.md) . Puede agregar otros elementos, como archivos HTML, archivos de encabezado, recursos o archivos de texto.

> [!NOTE]
> No es posible agregar clases ATL y solo pueden agregarse clases MFC en los tipos de aplicación de escritorio de Windows que sean compatibles con MFC (vea la tabla anterior).

Puede ver los archivos que el asistente crea para el proyecto en el **Explorador de soluciones**. Para obtener más información acerca de los archivos que crea el Asistente para el proyecto, vea el archivo de proyecto generado, `ReadMe.txt`. Para obtener más información sobre los tipos de archivo, consulte [Tipos de archivo creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Vea también

[Creación de una aplicación de escritorio de Windows vacía](../windows/creating-an-empty-windows-desktop-application.md)  
[Tipos de proyecto de Visual C++](../ide/visual-cpp-project-types.md)