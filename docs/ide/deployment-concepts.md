---
title: Conceptos de implementación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea2039cd9fa1c5071da143f557406d028f464d7e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676713"
---
# <a name="deployment-concepts"></a>Conceptos de implementación

En esta sección se explican las consideraciones principales para la implementación de aplicaciones de C++.

## <a name="windows-installer-deployment-in-c"></a>Implementación de Windows Installer en C++

En los proyectos de Visual C++ se suele usar el programa de instalación de Windows Installer tradicional para la implementación. Para preparar una implementación de Windows Installer, la aplicación se empaqueta en un archivo setup.exe y se distribuye ese archivo, junto con un paquete de instalador (.msi). Después, los usuarios ejecutan setup.exe para instalar la aplicación.

Para empaquetar la aplicación, se agrega un proyecto de instalación a la solución; cuando se compila, se crean los archivos de paquete de instalación y del instalador que se distribuyen a los usuarios. Para obtener más información, vea [Elegir un método de implementación](../ide/choosing-a-deployment-method.md).

## <a name="library-dependencies"></a>Dependencias de biblioteca

Cuando se compila una aplicación de C/C ++ mediante la funcionalidad proporcionada por las bibliotecas de Visual C++, depende de la presencia de esas bibliotecas en tiempo de ejecución. Para que la aplicación, se pueda ejecutar, se debe vincular, de manera estática o dinámica, a las bibliotecas de Visual C++ necesarias. Si una aplicación se vincula de manera dinámica a una biblioteca de Visual C++, cuando se ejecute, esa biblioteca debe estar presente para que se pueda cargar. Por otro lado, si la aplicación se vincula de manera estática a una biblioteca de Visual C++, no es necesario que los archivos DLL correspondientes estén presentes en el equipo del usuario. Pero la vinculación estática tiene algunos efectos negativos, por ejemplo, el aumento del tamaño de los archivos de aplicación y la dificultad de realizar el mantenimiento. Para obtener más información, vea [Ventajas de usar archivos DLL](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls).

## <a name="packaging-and-redistributing"></a>Empaquetado y redistribución

Las bibliotecas de Visual C++ se empaquetan como archivos DLL y Visual Studio instala todas las bibliotecas necesarias para las aplicaciones de C o C++ en el equipo del desarrollador. Pero al implementar la aplicación para los usuarios, en la mayoría de los casos no es factible que tengan que volver a instalar Visual Studio para poder ejecutar la aplicación. Es importante poder redistribuir solamente las partes de Visual C++ que son necesarias para que la aplicación se ejecute de forma correcta.

Para obtener más información sobre el empaquetado y la redistribución, vea los temas siguientes:

- [Determinar qué archivos DLL se redistribuirán](../ide/determining-which-dlls-to-redistribute.md).

- [Elegir un método de implementación](../ide/choosing-a-deployment-method.md).

- [Implementación de CRT universal](universal-crt-deployment.md).

Para obtener ejemplos de implementación y sugerencias sobre solución de problemas, vea:

- [Ejemplos de implementación](../ide/deployment-examples.md).

- [Solución de problemas de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

## <a name="see-also"></a>Vea también

- [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [Descripción de las dependencias de una aplicación de Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)

