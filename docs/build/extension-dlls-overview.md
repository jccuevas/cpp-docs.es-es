---
title: 'Archivos DLL de extensión: Información general'
ms.date: 05/06/2019
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: ea8e950e28907ea1a4a85c1f39392d5505f08c49
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221362"
---
# <a name="mfc-extension-dlls-overview"></a>Archivos DLL de extensión MFC: Información general

Un archivo DLL de extensión de MFC es un archivo DLL que implementa clases reutilizables derivadas de clases existentes de la biblioteca MFC (Microsoft Foundation Class). Los archivos DLL de extensión de MFC se compilan con la versión de biblioteca de vínculos dinámicos de MFC (conocida también como la versión compartida de MFC). Solo los archivos ejecutables de MFC (aplicaciones o archivos DLL estándar de MFC) integrados en la versión compartida de MFC pueden usar un archivo DLL de extensión de MFC. Mediante un archivo DLL de extensión de MFC, se pueden derivar nuevas clases personalizadas a partir de MFC y ofrecer esta versión extendida de MFC a las aplicaciones que llamen al archivo DLL.

También se puede utilizar archivos DLL de extensión para realizar transferencias de objetos derivados de MFC entre la aplicación y el archivo DLL. Las funciones miembro asociadas al objeto transferido existen en el módulo en que se creó el objeto. Dado que estas funciones se exportan correctamente al usar la versión compartida del archivo DLL de MFC, pueden pasarse punteros a objetos de MFC o derivados de MFC con libertad entre una aplicación y los archivos DLL de extensión de MFC que cargue.

Para obtener un ejemplo de un archivo DLL que cumple los requisitos básicos de un archivo DLL de extensión de MFC, vea el ejemplo [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) de MFC. En concreto, examine los archivos Testdll1.cpp y Testdll2.cpp.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Inicializar un archivo DLL de extensión de MFC](run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Archivos DLL de extensión MFC](extension-dlls.md)

- [Uso de archivos DLL de extensión MFC de base de datos, OLE y Sockets en archivos DLL de MFC estándar](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [DLL no basada en MFC: información general](non-mfc-dlls-overview.md)

- [Archivos DLL de MFC estándar vinculados estáticamente a MFC](regular-dlls-statically-linked-to-mfc.md)

- [Archivos DLL de MFC estándar vinculados dinámicamente a MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Creación de un archivo DLL de MFC](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>Vea también

[Tipos de archivos DLL](kinds-of-dlls.md)
