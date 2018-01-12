---
title: "Archivos DLL de extensión: Información general sobre | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 407ed0c63dce8e350c24ac5f260876fb6ab47576
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-extension-dlls-overview"></a>Archivos DLL de extensión MFC: información general
Una extensión MFC DLL es un archivo DLL que implementa clases reutilizables derivadas de clases de Microsoft Foundation Class Library existentes. Archivos DLL de extensión MFC se generan con la versión de biblioteca de vínculos dinámicos de MFC (conocida también como la versión compartida de MFC). Sólo archivos ejecutables MFC (aplicaciones o archivos DLL de MFC estándar) que se generan con la versión compartida de MFC pueden utilizar un archivo DLL de extensión MFC. Con un archivo DLL de extensión MFC, puede derivar nuevas clases personalizadas a partir de MFC y ofrecer esta versión extendida de MFC a las aplicaciones que llamen al archivo DLL.  
  
 También se puede utilizar archivos DLL de extensión para realizar transferencias de objetos derivados de MFC entre la aplicación y el archivo DLL. Las funciones miembro asociadas al objeto transferido existen en el módulo en que se creó el objeto. Dado que estas funciones se exportan correctamente al usar la versión compartida del archivo DLL de MFC, pueden pasarse MFC o punteros a objetos derivados de MFC entre la aplicación y la carga de DLL de extensión MFC.  
  
 Para obtener un ejemplo de un archivo DLL que satisfaga los requisitos básicos de un archivo DLL de extensión MFC, vea el ejemplo MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk). En concreto, examine los archivos Testdll1.cpp y Testdll2.cpp.  
  
 Tenga en cuenta que el término AFXDLL ya no se usa en la documentación de Visual C++. Un archivo DLL de extensión MFC tiene las mismas características que los antiguos archivos AFXDLL.  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Inicializar un archivo DLL de extensión MFC](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Archivos DLL de extensión MFC](../build/extension-dlls.md)  
  
-   [Uso de archivos DLL de extensión MFC de base de datos, OLE y Sockets en archivos DLL de MFC estándar](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Archivos DLL no basados en MFC: información general](../build/non-mfc-dlls-overview.md)  
  
-   [Archivos DLL de MFC estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL de MFC estándar vinculado dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Crear un archivo DLL de MFC](../mfc/reference/mfc-dll-wizard.md)  
  
## <a name="see-also"></a>Vea también  
 [Tipos de archivos DLL](../build/kinds-of-dlls.md)