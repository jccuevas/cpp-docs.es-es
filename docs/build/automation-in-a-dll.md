---
title: Automation en un archivo DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: dedc832d6726dccf8c0c2e88f9f4d5c67590c1c2
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220922"
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

[Crear archivos DLL de C o C++ en Visual Studio](dlls-in-visual-cpp.md)
