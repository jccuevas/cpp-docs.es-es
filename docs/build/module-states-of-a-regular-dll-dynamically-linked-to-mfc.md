---
title: "Estados de módulos de un archivo DLL de MFC estándar vinculado dinámicamente a MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b88f895255c698f04b6988e63b8b75372fa59b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>Estados de módulos de un archivo DLL de MFC estándar vinculado dinámicamente a MFC
La capacidad de vincular dinámicamente normal DLL de MFC con la DLL de MFC permite realizar algunas configuraciones que están muy complicadas. Por ejemplo, una DLL de MFC normal y el archivo ejecutable que lo usa pueden ambos vincular dinámicamente con la DLL de MFC y los archivos DLL de extensión MFC.  
  
 Esta configuración supone un problema con respecto a los datos globales de MFC, como el puntero al actual `CWinApp` objeto y asignaciones de identificadores.  
  
 Antes de la versión 4.0 de MFC, estos datos globales residían en la DLL de MFC propio y se comparten todos los módulos en el proceso. Dado que cada proceso que utiliza un archivo DLL para Win32 obtiene su propia copia de los datos de los archivos DLL, este esquema proporciona una forma sencilla de realizar un seguimiento de los datos por proceso. Además, dado que el modelo AFXDLL suponía que podría haber sólo uno `CWinApp` objeto y solo un conjunto de asignaciones en el proceso de identificadores, podrían realizar un seguimiento de estos elementos en la DLL de MFC propio.  
  
 Pero con la capacidad de vincular dinámicamente una DLL de MFC regulares a la DLL de MFC, ahora es posible tener dos o más `CWinApp` objetos en un proceso y también dos o más conjuntos de asignaciones de identificadores. ¿Cómo MFC realizar un seguimiento de los que debería estar utilizando?  
  
 La solución consiste en proporcionar su propia copia de esta información de estado global de cada módulo (aplicación o DLL de MFC normal). Por lo tanto, una llamada a **AfxGetApp** en regular DLL de MFC devuelve un puntero a la `CWinApp` objeto en el archivo DLL, no del archivo ejecutable. Esta copia por módulo de los datos globales de MFC se conoce como un estado del módulo y se describe en [Nota técnica 58 de MFC](../mfc/tn058-mfc-module-state-implementation.md).  
  
 El procedimiento de ventana común de MFC cambia automáticamente al estado de módulo correcto, por lo que no es necesario preocuparse de los controladores de mensajes implementados en la DLL de MFC normal. Pero cuando el ejecutable llama a la DLL de MFC normal, es necesario establecer explícitamente el estado actual del módulo en el otro para el archivo DLL. Para ello, use la **AFX_MANAGE_STATE** macro en cada función exportada desde el archivo DLL. Esto se realiza agregando la siguiente línea de código al principio de las funciones exportadas desde el archivo DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [Archivos DLL de MFC estándar vinculado dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Archivos DLL de extensión MFC](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)