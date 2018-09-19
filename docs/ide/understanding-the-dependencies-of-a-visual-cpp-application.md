---
title: Descripción de las dependencias de una aplicación de Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application deployment [C++], dependencies
- Dependency Walker
- dependencies [C++], application deployment and
- deploying applications [C++], dependencies
- DUMPBIN utility
- DLLs [C++], dependencies
- depends.exe
- libraries [C++], application deployment issues
ms.assetid: 62a44c95-c389-4c5f-82fd-07d7ef09dbf9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da2aadeba69a8be29627650ba6ef24516098a8e3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33338788"
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>Descripción de las dependencias de una aplicación de Visual C++
Para determinar de qué bibliotecas de Visual C++ depende una aplicación, puede ver las propiedades del proyecto. (En el Explorador de soluciones, haga clic con el botón derecho y seleccione **Propiedades** para abrir el cuadro de diálogo **Páginas de propiedades**). También puede usar Dependency Walker (depends.exe), que proporciona una imagen más completa de las dependencias.  
  
 En el cuadro de diálogo **Páginas de propiedades**, puede examinar las diversas páginas de **Propiedades de configuración** para entender las dependencias. Por ejemplo, si en el proyecto se usan las bibliotecas de MFC y se selecciona **Uso de MFC**, **Usar MFC en un archivo DLL compartido** en la página **General** de **Propiedades de configuración**, la aplicación en tiempo de ejecución depende de archivos DLL de MFC como mfc\<versión>.dll. Si en la aplicación no se usa MFC, es posible que dependa de la biblioteca CRT si se selecciona un valor de **Biblioteca en tiempo de ejecución** de **DLL de depuración multiproceso (/MDd)** o **DLL multiproceso (/MD)** en **Propiedades de configuración**, **C/C++**, **Generación de código**.  
  
 Una forma más completa de determinar los archivos DLL de los que depende la aplicación consiste en usar Dependency Walker (depends.exe) para abrirla. Puede descargar la herramienta desde el sitio web de [Dependency Walker](http://go.microsoft.com/fwlink/p/?LinkId=132640).  
  
 Con depends.exe, puede examinar una lista de archivos DLL que están vinculados a la aplicación en tiempo de carga, así como una lista de sus archivos DLL de carga retrasada. Si desea obtener una lista completa de los archivos DLL que se cargan dinámicamente en tiempo de ejecución, puede emplear la característica de generación de perfiles de depends.exe para probar la aplicación hasta que esté seguro de que se han usado todas las rutas de acceso de código. Al finalizar la sesión de generación de perfiles, depends.exe mostrará qué archivos DLL se cargaron dinámicamente durante el tiempo de ejecución.  
  
 Cuando use depends.exe, tenga en cuenta que un archivo DLL puede tener una dependencia en otro archivo DLL o en una versión concreta de un archivo DLL. Puede utilizar depends.exe en el equipo de desarrollo o en un equipo de destino. En el equipo de desarrollo, depends.exe indica qué archivos DLL son necesarios para admitir una aplicación. Si tiene problemas para ejecutar una aplicación en un equipo de destino, puede copiar depends.exe en él y abrir la aplicación en la herramienta para poder determinar si algunos archivos DLL necesarios faltan o son incorrectos.  
  
 Una vez que sepa de qué archivos DLL depende la aplicación, puede determinar cuáles deben redistribuirse con la aplicación al realizar la implementación en otro equipo. En la mayoría de los casos, no es necesario redistribuir los archivos DLL del sistema, pero es posible que tenga que redistribuirlos para las bibliotecas de Visual C++. Para obtener más información, vea [Determinar qué archivos DLL se redistribuirán](../ide/determining-which-dlls-to-redistribute.md).  
  
## <a name="see-also"></a>Vea también  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)