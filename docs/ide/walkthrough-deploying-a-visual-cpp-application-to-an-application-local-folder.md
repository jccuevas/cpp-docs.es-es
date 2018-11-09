---
title: Implementar una aplicación de Visual C++ en una carpeta local de la aplicación
ms.date: 09/17/2018
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
ms.openlocfilehash: 6715dacf6e00aacf3ba3ef7e6cd3773f48fd8e2f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596916"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Tutorial: Implementar una aplicación de Visual C++ en una carpeta local de la aplicación

Se describe cómo implementar una aplicación de Visual C++ copiando archivos en su carpeta.

## <a name="prerequisites"></a>Requisitos previos

- Un equipo con Visual Studio instalado.

- Otro equipo que no tenga las bibliotecas de Visual C++.

### <a name="to-deploy-an-application-to-an-application-local-folder"></a>Para implementar una aplicación en una carpeta local de aplicación

1. Cree y compile una aplicación MFC siguiendo los pasos de [Tutorial: Implementar una aplicación de Visual C++ mediante un proyecto de instalación](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Copie los archivos de biblioteca de MFC y de tiempo de ejecución de C (CRT) adecuados desde el directorio de instalación de Visual Studio en la carpeta \\VC\\redist\\*version* y, a continuación, péguelos en la carpeta \Release\ de un proyecto de MFC. Para obtener más información sobre otros archivos que es posible que tenga que copiar, vea [Determinar qué archivos DLL se redistribuirán](determining-which-dlls-to-redistribute.md).

1. Ejecute la aplicación MFC en un segundo equipo que no tenga las bibliotecas de Visual C++.

   1. Copie el contenido de la carpeta \Release\ y péguelo en la carpeta de aplicación en el segundo equipo.

   1. Ejecute la aplicación en el segundo equipo.

   La aplicación se ejecuta correctamente porque las bibliotecas de Visual C++ están disponibles en la carpeta local de la aplicación.

## <a name="see-also"></a>Vea también

[Ejemplos de implementación](deployment-examples.md)<br/>
