---
title: Automatización en un archivo DLL | Microsoft Docs
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
ms.openlocfilehash: cde5d0e400f1bdd3f5a851d47da581380273b04a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717795"
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

[Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)