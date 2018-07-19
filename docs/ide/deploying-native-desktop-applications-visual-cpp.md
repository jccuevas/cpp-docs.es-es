---
title: Implementar aplicaciones de escritorio nativas (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f4aa355c132b4c94f085cbdf7aa73785357d0f0
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34259249"
---
# <a name="deploying-native-desktop-applications-visual-c"></a>Implementar aplicaciones de escritorio nativas (Visual C++)

La implementación es el proceso mediante el cual se distribuye una aplicación o un componente acabado para instalarse en otros equipos. La planeación de la implementación se inicia cuando se crea una aplicación en el equipo de un desarrollador. La implementación finaliza cuando se instala la aplicación y está preparada para ejecutarse en el equipo del usuario.

Visual Studio proporciona diferentes tecnologías para implementar aplicaciones Windows. Entre ellas se incluyen las implementaciones ClickOnce y Windows Installer.

- ClickOnce se puede usar para implementar aplicaciones de C++ destinadas a Common Language Runtime (CLR): ensamblados mixtos, puros y comprobables. Aunque se puede usar Windows Installer para implementar una aplicación administrada, se recomienda usar ClickOnce porque aprovecha las características de seguridad de .NET Framework, como la firma de manifiestos. ClickOnce no admite la implementación de aplicaciones de C++ nativas. Para obtener más información, vea [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md).

- La tecnología de Windows Installer puede usarse para implementar aplicaciones de C++ nativas o aplicaciones de C++ orientadas a CLR.

Los artículos de esta sección de la documentación explican cómo asegurarse de que una aplicación de Visual C++ nativa se ejecute en cualquier equipo que proporciona una plataforma de destino admitida, cuyos archivos se deben incluir en un paquete de instalación, así como los métodos recomendados para redistribuir los componentes que dependen la aplicación.

## <a name="in-this-section"></a>En esta sección

- [Implementación en Visual C++](../ide/deployment-in-visual-cpp.md)

- [Conceptos de implementación](../ide/deployment-concepts.md)

- [Descripción de las dependencias de una aplicación de Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)

- [Determinar qué archivos DLL se redistribuirán](../ide/determining-which-dlls-to-redistribute.md)

- [Elegir un método de implementación](../ide/choosing-a-deployment-method.md)

- [Implementación de CRT universal](universal-crt-deployment.md).

- [Redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md)

- [Ejemplos de implementación](../ide/deployment-examples.md)

- [Redistribuir aplicaciones cliente web](../ide/redistributing-web-client-applications.md)

- [Implementación de ClickOnce para aplicaciones de Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md)

- [Ejecutar una aplicación /clr de C++ en una versión anterior del Runtime](../ide/running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>Secciones relacionadas

- [Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [Implementación](/dotnet/framework/deployment/index)

- [Solución de problemas de aplicaciones aisladas y ensamblados simultáneos de C/C++](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)