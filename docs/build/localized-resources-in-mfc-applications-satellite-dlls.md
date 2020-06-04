---
title: 'Recursos localizados en aplicaciones MFC: archivos DLL satélite'
ms.date: 11/04/2016
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
ms.openlocfilehash: 1f512cc17832564b5eb530b97f8bfb2642c43d43
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220743"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Recursos localizados en aplicaciones MFC: archivos DLL satélite

En MFC 7.0 y versiones posteriores se proporciona compatibilidad mejorada con los archivos DLL satélite, una característica que ayuda a crear aplicaciones en múltiples idiomas. Un archivo DLL satélite es una [DLL solo de recursos](creating-a-resource-only-dll.md) que contiene los recursos de una aplicación localizados para un idioma determinado. Cuando se inicia la ejecución de la aplicación, MFC carga de forma automática el recurso localizado más apropiado para el entorno. Por ejemplo, puede tener una aplicación con recursos en inglés con dos archivos DLL satélite, uno que contenga una traducción en francés de los recursos y otro con una traducción en alemán. Cuando la aplicación se ejecuta en un sistema en inglés, usa los recursos en inglés. Si se ejecuta en un sistema en francés, usa los recursos en francés; si se ejecuta en un sistema alemán, usa los recursos en alemán.

Para admitir recursos localizados en una aplicación MFC, MFC intenta cargar un archivo DLL satélite que contiene recursos localizados en un idioma concreto. Los archivos DLL satélite se denominan *NombreDeAplicaciónXXX*.dll, donde *NombreDeAplicación* es el nombre del archivo .exe o .dll que usa MFC, y *XXX* es el código de tres letras del idioma de los recursos (por ejemplo, "ESN" o "DEU").

MFC intenta cargar el archivo DLL de recursos para cada uno de los idiomas siguientes en orden y se detiene cuando encuentra uno:

1. El idioma predeterminado de la interfaz de usuario del usuario actual, tal y como lo devuelve la API GetUserDefaultUILanguage() de Win32.

1. El idioma predeterminado de la interfaz de usuario del usuario actual, sin ningún subidioma específico (es decir, ENC [inglés de Canadá] se convierte en ENU [inglés de EE. UU.]).

1. El idioma predeterminado de la interfaz de usuario del sistema, tal y como devuelve la API GetSystemDefaultUILanguage(). En otras plataformas, es el idioma del propio sistema operativo.

1. El idioma predeterminado de la interfaz de usuario del sistema, sin ningún subidioma específico.

1. Un idioma falso con el código LOC de tres letras.

Si MFC no encuentra ningún archivo DLL satélite, usa los recursos incluidos en la propia aplicación.

Por ejemplo, imagine que una aplicación LangExample.exe usa MFC y se ejecuta en un sistema de con varias interfaces de usuario; el idioma de la interfaz de usuario del sistema es ENU [inglés de EE. UU.] y el idioma de la interfaz de usuario del usuario actual está establecido en FRC [francés de Canadá]. MFC busca los archivos DLL siguientes en este orden:

1. LangExampleFRC.dll (idioma de la interfaz de usuario del usuario).

1. LangExampleFRA.dll (idioma de la interfaz de usuario del usuario sin el subidioma, en este ejemplo Francés (Francia).

1. LangExampleENU.dll (idioma de la interfaz de usuario del sistema).

1. LangExampleLOC.dll.

Si no se encuentra ninguno de estos archivos DLL, MFC usa los recursos de LangExample.exe.

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)<br/>
[TN057: Localización de componentes de MFC](../mfc/tn057-localization-of-mfc-components.md)
