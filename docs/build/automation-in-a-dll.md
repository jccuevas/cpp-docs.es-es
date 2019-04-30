---
title: Automation en un archivo DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: 4ac60c44348ea21f490cb312285ae88ac682cf7d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341662"
---
# <a name="automation-in-a-dll"></a>Automation en un archivo DLL

Al elegir la opción de automatización en el Asistente para archivos DLL de MFC, el asistente le proporciona lo siguiente:

- Un lenguaje de descripción del objeto de inicio (. Archivos ODL)

- Una directiva de inclusión en el archivo STDAFX.h para Afxole.h

- Una implementación de la `DllGetClassObject` función, que llama el **AfxDllGetClassObject** (función)

- Una implementación de la `DllCanUnloadNow` función, que llama el **AfxDllCanUnloadNow** (función)

- Una implementación de la `DllRegisterServer` función, que llama el [COleObjectFactory:: UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) (función)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Servidores de automatización](../mfc/automation-servers.md)

## <a name="see-also"></a>Vea también

[Archivos DLL en Visual C++](dlls-in-visual-cpp.md)
