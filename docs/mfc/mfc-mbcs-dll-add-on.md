---
title: Complemento DLL de MBCS de MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 1/04/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS
- MFC
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df6ecf03a5b1c92dc7e435fc014615db09422638
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-mbcs-dll-add-on"></a>Complemento DLL de MBCS para MFC

Compatibilidad con MFC y sus bibliotecas de juegos de caracteres multibyte (MBCS) conjunto requiere un paso adicional durante la instalación de Visual Studio en Visual Studio 2013, 2015 y 2017.

**Visual Studio 2013**: de forma predeterminada, las bibliotecas MFC instaladas de Visual Studio 2013 solo admiten el desarrollo de Unicode. Necesita los archivos DLL de MBCS para compilar un proyecto MFC en Visual Studio 2013 que tenga el **del juego de caracteres** propiedad establecida en **utilizar juego de caracteres multibyte** o **no establece**. Descargar el archivo DLL [biblioteca MFC Multibyte para Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770).

**Visual Studio 2015**: tanto Unicode y MBCS DLL de MFC se incluyen en los componentes del programa de instalación de Visual C++, pero la compatibilidad con MFC no está instalado de forma predeterminada. Visual C++ y MFC son configuraciones de instalación opcional en el programa de instalación de Visual Studio. Para asegurarse de que MFC está instalado, elija **Personalizado** en el programa de instalación y en **Lenguajes de programación**, asegúrese de que estén seleccionadas las opciones **Visual C++** y **Microsoft Foundation Classes para C++** . Si ya instaló Visual Studio, se le pedirá que instale Visual C++ o MFC cuando intente crear un proyecto MFC.

**Visual Studio de 2017**: el Unicode y MBCS DLL de MFC se instalan con el **desarrollo de escritorio con C++** cargas de trabajo cuando se selecciona **MFC y ATL son compatibles con** desde el **opcional Componentes** panel. Si la instalación no incluye estos componentes, puede iniciar el instalador desde el **nuevos proyectos** diálogo mediante el uso de la **abrir Visual Studio Installer** vínculo.

## <a name="see-also"></a>Vea también

[Versiones de la biblioteca MFC](../mfc/mfc-library-versions.md)

