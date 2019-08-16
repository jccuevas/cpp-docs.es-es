---
title: Complemento DLL de MBCS para MFC
ms.date: 05/08/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: 20145b200a0f8bac8ccb461331d4d233a3b0251e
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524818"
---
# <a name="mfc-mbcs-dll-add-on"></a>Complemento DLL de MBCS para MFC

Compatibilidad con MFC y sus bibliotecas de juegos de caracteres multibyte (MBCS) del conjunto requiere un paso adicional durante la instalación de Visual Studio en Visual Studio 2013 y versiones posteriores.

**Visual Studio 2013**: De forma predeterminada, las bibliotecas MFC instaladas en Visual Studio 2013 solo admiten el desarrollo de Unicode. Necesita las DLL de MBCS para compilar un proyecto MFC en Visual Studio 2013 que tenga el **del juego de caracteres** propiedad establecida en **utilizar juego de caracteres multibyte** o **Nenastaveno**. Descargue el archivo DLL en [Multibyte MFC Library para Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770).

**Visual Studio 2015**: Unicode y MBCS DLL de MFC se incluyen en los componentes de instalación de Visual C++, pero la compatibilidad con MFC no está instalado de forma predeterminada. Visual C++ y MFC son configuraciones de instalación opcional en el programa de instalación de Visual Studio. Para asegurarse de que MFC está instalado, elija **Personalizado** en el programa de instalación y en **Lenguajes de programación**, asegúrese de que estén seleccionadas las opciones **Visual C++** y **Microsoft Foundation Classes para C++** . Si ya instaló Visual Studio, se le pedirá que instale Visual C++ o MFC cuando intente crear un proyecto MFC.

**Visual Studio 2017 y versiones posteriores**: El Unicode y MBCS DLL de MFC se instalan con el **desarrollo de escritorio con C++** carga de trabajo cuando se selecciona **compatibilidad MFC y ATL** desde el **componentes opcionales** panel. Si la instalación no incluye estos componentes, navegue hasta la **archivo | Los proyectos nuevos** cuadro de diálogo y haga clic en el **abrir Visual Studio Installer** vínculo.

## <a name="see-also"></a>Vea también

[Versiones de la biblioteca MFC](../mfc/mfc-library-versions.md)
