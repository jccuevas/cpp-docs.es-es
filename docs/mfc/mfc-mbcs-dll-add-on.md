---
title: Complemento DLL de MBCS para MFC
ms.date: 12/02/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: fe74e0639664b6a6a86a4c3269f174de441002f4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810371"
---
# <a name="mfc-mbcs-dll-add-on"></a>Complemento DLL de MBCS para MFC

La compatibilidad con MFC y sus bibliotecas de juegos de caracteres multibyte (MBCS) requiere un paso adicional durante la instalación de Visual Studio en Visual Studio 2013 y versiones posteriores.

**Visual Studio 2013**: de forma predeterminada, las bibliotecas MFC instaladas en Visual Studio 2013 admiten únicamente el desarrollo Unicode. Necesita los archivos dll de MBCS para compilar un proyecto MFC en Visual Studio 2013 que tenga la propiedad juego de **caracteres** establecida en **utilizar juego de caracteres multibyte** o **sin establecer**. Descargue el archivo DLL en la [biblioteca MFC multibyte para Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770).

**Visual Studio 2015**: los archivos dll de MFC Unicode y MBCS se incluyen en C++ los componentes del programa de instalación visual, pero la compatibilidad con MFC no se instala de forma predeterminada. Visual C++ y MFC son configuraciones de instalación opcional en el programa de instalación de Visual Studio. Para asegurarse de que MFC está instalado, elija **Personalizado** en el programa de instalación y en **Lenguajes de programación**, asegúrese de que estén seleccionadas las opciones **Visual C++** y **Microsoft Foundation Classes para C++** . Si ya instaló Visual Studio, se le pedirá que instale Visual C++ o MFC cuando intente crear un proyecto MFC.

**Visual Studio 2017 y versiones posteriores**: los archivos dll de MFC de Unicode y MBCS se instalan con el **desarrollo de escritorio C++ con** carga de trabajo cuando se selecciona **compatibilidad con MFC y ATL** en el panel **componentes opcionales** del programa instalador de Visual Studio. Si la instalación no incluye estos componentes, desplácese hasta el **archivo |** Cuadro de diálogo nuevos proyectos y haga clic en el vínculo **abrir instalador de Visual Studio** . Para obtener más información, vea [instalar Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="see-also"></a>Vea también

[Versiones de la biblioteca MFC](../mfc/mfc-library-versions.md)
