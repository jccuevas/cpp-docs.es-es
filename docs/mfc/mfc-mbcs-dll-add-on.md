---
title: Complemento DLL de MBCS de MFC | Documentos de Microsoft
ms.custom: 
ms.date: 08/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MBCS
- MFC
ms.assetid: bebec0ff-e019-42ca-b5df-8c218ac5b54a
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 176ed47b4d6a799cf53d2a1cea8cb232f1c2c4aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-mbcs-dll-add-on"></a>Complemento DLL de MBCS para MFC
 Las DLL multibyte son necesarias para compilar un proyecto MFC en Visual Studio 2015 que tenga la propiedad **Juego de caracteres** establecida en **Utilizar juego de caracteres multibyte** o **Sin establecer**.  

**Visual Studio 2013**: descargar el archivo DLL [biblioteca MFC Multibyte para Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770).

**Visual Studio 2015**: el archivo DLL se incluye en los componentes del programa de instalación de Visual C++. Visual C++ y MFC son configuraciones de instalación opcional en el programa de instalación de Visual Studio. Para asegurarse de que MFC está instalado, elija **Personalizado** en el programa de instalación y en **Lenguajes de programación**, asegúrese de que estén seleccionadas las opciones **Visual C++** y **Microsoft Foundation Classes para C++** . Si ya instaló Visual Studio, se le pedirá que instale Visual C++ o MFC cuando intente crear un proyecto MFC.  
  
**2017 de Visual Studio**: la DLL se instala con el **desarrollo de escritorio con C++** carga de trabajo cuando se selecciona **compatibilidad MFC y ATL** desde el **decomponentesopcionales** panel.

  
## <a name="see-also"></a>Vea también  
 [Versiones de la biblioteca MFC](../mfc/mfc-library-versions.md)

