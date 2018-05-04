---
title: Automatización en un archivo DLL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41c5f31a72cf734296ecb281e0785d415c8043a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="automation-in-a-dll"></a>Automation en un archivo DLL
Al elegir la opción de automatización en el Asistente para archivos DLL de MFC, el asistente proporciona lo siguiente:  
  
-   Un lenguaje de descripción del objeto de inicio (. Archivo ODL)  
  
-   Una directiva de inclusión en el archivo STDAFX.h para Afxole.h  
  
-   Una implementación de la `DllGetClassObject` función, que llama a la **AfxDllGetClassObject** (función)  
  
-   Una implementación de la `DllCanUnloadNow` función, que llama a la **AfxDllCanUnloadNow** (función)  
  
-   Una implementación de la `DllRegisterServer` función, que llama a la [:: UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) (función)  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Servidores de automatización](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)