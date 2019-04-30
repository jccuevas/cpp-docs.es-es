---
title: Descripción de las dependencias de una aplicación de Visual C++
ms.date: 11/04/2016
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
ms.openlocfilehash: 92db11778de7d31bbab67e649cd58e264da331e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387859"
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>Descripción de las dependencias de una aplicación de Visual C++

Para determinar de qué bibliotecas de Visual C++ depende una aplicación, puede ver las propiedades del proyecto. (En el Explorador de soluciones, haga clic con el botón derecho y seleccione **Propiedades** para abrir el cuadro de diálogo **Páginas de propiedades**). En Windows 8 y versiones anteriores, también puede usar Dependency Walker (depends.exe), que ofrece una imagen más completa de las dependencias. Para las versiones más recientes de Windows la [lucasg/dependencias](https://github.com/lucasg/Dependencies) herramienta proporciona una funcionalidad similar (Esto es una herramienta de terceros no garantizada por Microsoft).

En el cuadro de diálogo **Páginas de propiedades**, puede examinar las diversas páginas de **Propiedades de configuración** para entender las dependencias. Por ejemplo, si en el proyecto se usan las bibliotecas de MFC y se selecciona **Uso de MFC**, **Usar MFC en un archivo DLL compartido** en la página **General** de **Propiedades de configuración**, la aplicación en tiempo de ejecución depende de archivos DLL de MFC como mfc\<versión>.dll. Si en la aplicación no se usa MFC, es posible que dependa de la biblioteca CRT si se selecciona un valor de **Biblioteca en tiempo de ejecución** de **DLL de depuración multiproceso (/MDd)** o **DLL multiproceso (/MD)** en **Propiedades de configuración**, **C/C++**, **Generación de código**.

Con depends.exe, puede examinar una lista de archivos DLL que están vinculados a la aplicación en tiempo de carga, así como una lista de sus archivos DLL de carga retrasada. Si desea obtener una lista completa de los archivos DLL que se cargan dinámicamente en tiempo de ejecución, puede emplear la característica de generación de perfiles de depends.exe para probar la aplicación hasta que esté seguro de que se han usado todas las rutas de acceso de código. Al finalizar la sesión de generación de perfiles, depends.exe mostrará qué archivos DLL se cargaron dinámicamente durante el tiempo de ejecución.

Cuando use depends.exe, tenga en cuenta que un archivo DLL puede tener una dependencia en otro archivo DLL o en una versión concreta de un archivo DLL. Puede utilizar depends.exe en el equipo de desarrollo o en un equipo de destino. En el equipo de desarrollo, depends.exe indica qué archivos DLL son necesarios para admitir una aplicación. Si tiene problemas para ejecutar una aplicación en un equipo de destino, puede copiar depends.exe en él y abrir la aplicación en la herramienta para poder determinar si algunos archivos DLL necesarios faltan o son incorrectos.

Una vez que sepa de qué archivos DLL depende la aplicación, puede determinar cuáles deben redistribuirse con la aplicación al realizar la implementación en otro equipo. En la mayoría de los casos, no es necesario redistribuir los archivos DLL del sistema, pero es posible que tenga que redistribuirlos para las bibliotecas de Visual C++. Para obtener más información, vea [Determinar qué archivos DLL se redistribuirán](determining-which-dlls-to-redistribute.md).

## <a name="see-also"></a>Vea también

[Implementar aplicaciones de escritorio](deploying-native-desktop-applications-visual-cpp.md)
