---
title: "Recursos localizados en aplicaciones MFC: archivos DLL satélite | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc97e73998c581a40ed7d344b1ade5ca90b94ac2
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Recursos localizados en aplicaciones MFC: archivos DLL satélite
La versión MFC 7.0 y posterior proporciona compatibilidad mejorada con archivos DLL satélite, una característica que le ayuda a crear aplicaciones en varios idiomas. Una licencia de satélite DLL es un [archivo DLL de recursos](../build/creating-a-resource-only-dll.md) que contiene los recursos de una aplicación localizados para un idioma determinado. Cuando la aplicación empieza a ejecutarse, MFC carga automáticamente el recurso localizado más adecuado para el entorno. Por ejemplo, podría tener una aplicación con recursos del idioma inglés con dos archivos DLL satélite, uno que contiene una traducción al francés de los recursos y otra que contiene una traducción de alemán. Cuando la aplicación se ejecuta en un sistema de idioma inglés, utiliza los recursos en inglés. Si se ejecuta en un sistema francés, utiliza los recursos en francés; Si se ejecutan en un sistema en alemán, utiliza los recursos de alemán.  
  
 Para admitir recursos localizados en una aplicación MFC, MFC intenta cargar un archivo DLL satélite que contienen recursos localizados en un idioma determinado. Archivos DLL satélite se denomina *NombreAplicaciónXXX*.dll, donde *ApplicationName* es el nombre del .exe o .dll que utiliza MFC, y *XXX* es el código de tres letras del idioma de los recursos (por ejemplo, 'ENU' o 'DEU').  
  
 MFC intenta cargar la DLL de recursos para cada uno de los siguientes idiomas en orden, deteniéndose cuando encuentra uno:  
  
1. El idioma del usuario actual predeterminado interfaz de usuario, tal como lo devuelve a través de la API de Win32 GetUserDefaultUILanguage().  
  
2.  Idioma de interfaz de usuario predeterminado del usuario actual, sin ningún sublenguaje específico (es decir, ENC [inglés canadiense] se convierte en ESN [EE. UU. Inglés]).  
  
3.  El idioma predeterminado del sistema interfaz de usuario, tal como lo devuelve la API GetSystemDefaultUILanguage(). En otras plataformas, es el idioma del sistema operativo propio.  
  
4.  El idioma predeterminado del sistema interfaz de usuario, sin ningún sublenguaje específico.  
  
5.  Un lenguaje falso con el código de 3 letras loc.  
  
 Si MFC no encuentra ningún archivo DLL satélite, utiliza los recursos están contenidos en la propia aplicación.  
  
 Por ejemplo, suponga que una aplicación LangExample.exe utiliza MFC y se está ejecutando en un sistema de interfaz de usuario múltiple; el idioma de interfaz de usuario del sistema es ENU [EE. UU. Inglés] y el idioma de interfaz de usuario del usuario actual se establece en FRC [francés canadiense]. MFC busca los siguientes archivos DLL en el siguiente orden:  
  
1.  LangExampleFRC.dll (idioma de interfaz de usuario del usuario).  
  
2.  LangExampleFRA.dll (idioma de interfaz de usuario del usuario sin sublenguaje, en este ejemplo, francés (Francia).  
  
3.  LangExampleENU.dll (idioma de interfaz de usuario del sistema).  
  
4.  LangExampleLOC.dll.  
  
 Si no encuentra ninguno de estos archivos DLL, MFC usa los recursos de LangExample.exe.  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)   
 [TN057: Localización de componentes de MFC](../mfc/tn057-localization-of-mfc-components.md)