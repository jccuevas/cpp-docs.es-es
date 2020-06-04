---
title: Estados del módulo de un archivo DLL de MFC estándar vinculado dinámicamente a MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
ms.openlocfilehash: cedce676f5586369446c9856fd33e4d16c237b27
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220582"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>Estados del módulo de un archivo DLL de MFC estándar vinculado dinámicamente a MFC

La capacidad de vincular dinámicamente un archivo DLL de MFC estándar al archivo DLL de MFC permite algunas configuraciones muy complicadas. Por ejemplo, un archivo DLL de MFC estándar y el ejecutable que lo usa se pueden vincular de forma dinámica al archivo DLL de MFC y a cualquier DLL con la extensión de MFC.

Esta configuración plantea un problema con respecto a los datos globales de MFC, como el puntero al objeto `CWinApp` actual y asignaciones de identificadores.

Antes de la versión 4.0 de MFC, estos datos globales residían en el propio archivo DLL de MFC y los compartían todos los módulos del proceso. Como cada proceso en el que se usa un archivo DLL de Win32 obtiene su propia copia de los datos del archivo DLL, este esquema proporcionaba una manera sencilla de realizar el seguimiento de los datos por proceso. Además, como el modelo AFXDLL presuponía que solo hubiera un objeto `CWinApp` y solo un conjunto de asignaciones de identificadores en el proceso, el seguimiento de estos elementos se podía realizar en el propio archivo DLL de MFC.

Pero con la capacidad de vincular de forma dinámica un archivo DLL de MFC estándar al archivo DLL de MFC, ahora es posible tener dos o más objetos `CWinApp` en un proceso, además de dos o más conjuntos de asignaciones de identificadores. ¿Cómo realiza MFC el seguimiento de cuáles se deben usar?

La solución consiste en proporcionar a cada módulo (aplicación o DLL de MFC estándar) su propia copia de esta información de estado global. Por tanto, una llamada a **AfxGetApp** en el archivo DLL de MFC estándar devuelve un puntero al objeto `CWinApp` en el archivo DLL, no al del ejecutable. Esta copia por módulo de los datos globales de MFC se conoce como estado del módulo y se describe en la [Nota técnica 58 de MFC](../mfc/tn058-mfc-module-state-implementation.md).

El procedimiento de ventana común de MFC cambia automáticamente al estado correcto del módulo, por lo que no es necesario preocuparse por él en los controladores de mensajes implementados en el archivo DLL de MFC estándar. Pero, cuando el ejecutable llama al archivo DLL de MFC estándar, debe establecer de forma explícita el estado actual del módulo en el del archivo DLL. Para ello, use la macro **AFX_MANAGE_STATE** en todas las funciones exportadas desde el archivo DLL. Para hacerlo, agregue la línea de código siguiente al principio de las funciones exportadas desde el archivo DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Administración de los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Archivos DLL de extensión MFC](extension-dlls-overview.md)

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
