---
title: 'Recursos localizados en aplicaciones MFC: Archivos DLL satélite'
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
ms.openlocfilehash: d479599acceac29f0f2ee54857c663c81a919acf
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420406"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Recursos localizados en aplicaciones MFC: Archivos DLL satélite

Versión MFC 7.0 y versiones posterior proporciona compatibilidad mejorada para archivos DLL satélite, una característica que le ayuda a crear aplicaciones en varios idiomas. Una licencia satélite DLL es un [archivo DLL de recursos](../build/creating-a-resource-only-dll.md) que contiene los recursos de una aplicación localizados en un idioma determinado. Cuando la aplicación empieza a ejecutarse, MFC carga automáticamente el recurso localizado más adecuado para el entorno. Por ejemplo, podría tener una aplicación con recursos del idioma inglés con dos archivos DLL satélite, uno que contiene una traducción al francés de sus recursos y la otra que contiene una traducción de alemán. Cuando la aplicación se ejecuta en un sistema de idioma inglés, utiliza los recursos en inglés. Si se ejecuta en un sistema en francés, usa los recursos en francés; Si se ejecuta en un sistema en alemán, usa los recursos de alemán.

Para admitir recursos localizados en una aplicación MFC, MFC intenta cargar un archivo DLL satélite que contiene recursos localizados en un idioma determinado. Archivos DLL satélite se denominan *NombreAplicaciónXXX*.dll, donde *ApplicationName* es el nombre del .exe o .dll que utiliza MFC, y *XXX* es el código de tres letras del idioma los recursos (por ejemplo, 'ENU' o 'DEU').

MFC intenta cargar la DLL de recursos para cada uno de los idiomas siguientes en orden, deteniéndose cuando encuentra uno:

1. UI idioma predeterminado del usuario actual, tal como lo devuelve la API de Win32 GetUserDefaultUILanguage().

1. Idioma de interfaz de usuario predeterminado del usuario actual, sin ningún sublenguaje específico (es decir, ENC [inglés canadiense] se convierte en ESN [EE. UU. En inglés]).

1. El idioma predeterminado del sistema la interfaz de usuario, tal como lo devuelve la API GetSystemDefaultUILanguage(). En otras plataformas, esto es el idioma del propio sistema operativo.

1. El idioma predeterminado del sistema la interfaz de usuario, sin ningún sublenguaje específico.

1. Un lenguaje falso con el código de 3 letras loc.

MFC no encuentra ningún archivo DLL satélite, utiliza los recursos están contenidos en la propia aplicación.

Por ejemplo, suponga que una aplicación LangExample.exe utiliza MFC y se está ejecutando en un sistema de la interfaz de usuario múltiple; el idioma de interfaz de usuario del sistema es ENU [EE. UU. Inglés] y el idioma de interfaz de usuario del usuario actual se establece en FRC [francés canadiense]. MFC busca los siguientes archivos DLL en el orden siguiente:

1. LangExampleFRC.dll (idioma de interfaz de usuario del usuario).

1. LangExampleFRA.dll (idioma de interfaz de usuario del usuario sin sublenguaje, en este ejemplo, francés (Francia).

1. LangExampleENU.dll (idioma de interfaz de usuario del sistema).

1. LangExampleLOC.dll.

Si se encuentra ninguno de estos archivos DLL, MFC utiliza los recursos de LangExample.exe.

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)<br/>
[TN057: Localización de componentes de MFC](../mfc/tn057-localization-of-mfc-components.md)
