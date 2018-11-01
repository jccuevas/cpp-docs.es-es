---
title: MFC y ATL
ms.date: 01/24/2018
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
ms.openlocfilehash: 620d514e1bc1bad6c33eab16577639c4053cdf10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486364"
---
# <a name="mfc-and-atl"></a>MFC y ATL

Microsoft Foundation Classes (MFC) proporciona un contenedor de orientado a objetos de C++ a través de Win32 para el desarrollo rápido de aplicaciones de escritorio nativas. Active Template Library (ATL) es una biblioteca de contenedor que simplifica el desarrollo de COM y se usa ampliamente para crear controles ActiveX.

Se pueden crear programas MFC o ATL con Visual Studio Community Edition o superior. Las ediciones Express no admiten MFC o ATL.

En Visual Studio 2015, Visual C++ es un componente opcional y los componentes MFC y ATL son subcomponentes opcionales en Visual C++. Si no selecciona estos componentes durante la instalación inicial de Visual Studio, se le pedirá que los instale la primera vez que intente crear o abrir un proyecto MFC o ATL.

En Visual Studio 2017 y versiones posteriores, MFC y ATL son subcomponentes opcionales en el **desarrollo de escritorio con C++** carga de trabajo en el programa instalador de Visual Studio. Puede instalar la compatibilidad ATL sin MFC, o combinar la compatibilidad con ATL y MFC (MFC depende de ATL). Para obtener más información acerca de las cargas de trabajo y componentes, vea [instalar Visual Studio 2017](/visualstudio/install/install-visual-studio).

## <a name="related-articles"></a>Artículos relacionados

|Título|Descripción|
|-----------|-----------------|
|[Aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md)|Microsoft Foundation Classes proporciona un contenedor fino orientado a objetos en Win32 para habilitar el desarrollo rápido de aplicaciones GUI en C++.|
|[Componentes de escritorio COM de ATL](../atl/atl-com-desktop-components.md)|ATL proporciona plantillas de clase y construcciones para otros usos con el fin de simplificar la creación de objetos COM en C++.|
|[Clases compartidas ATL y MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Referencias de [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) y otras clases que MFC y ATL comparten.|
|[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)|El editor de recursos permite editar los recursos de la interfaz de usuario, como cadenas, imágenes y cuadros de diálogo.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Tema primario para todo el contenido de C++ en MSDN Library.|