---
title: Convenciones de nomenclatura para archivos DLL de MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC libraries [C++], naming conventions
- naming conventions [C++], MFC DLLs
- MFC DLLs [C++], naming conventions
- libraries [C++], MFC DLL names
- shared DLL versions [C++]
- DLLs [C++], naming conventions
- DLLs [C++], library names
ms.assetid: 0db9c3f3-87d3-40e8-8964-250f9d2a2209
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4f7702e9babcc4769136d6deab63b627f8b09bd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="naming-conventions-for-mfc-dlls"></a>Convenciones de nomenclatura para archivos DLL de MFC
Los archivos DLL y las bibliotecas incluidos en MFC utilizan una convención de nomenclatura estructurada. Esto hace más fácil saber qué archivo DLL o la biblioteca debe utilizar para cada propósito.  
  
 Las bibliotecas de importación necesarias para generar aplicaciones o archivos DLL de extensión MFC que utilicen estos archivos DLL tienen el mismo nombre base que el archivo DLL, pero tienen una extensión de nombre de archivo .lib.  
  
### <a name="shared-dll-naming-convention"></a>Archivo DLL compartido Convención de nomenclatura  
  
|Archivo DLL|Descripción|  
|---------|-----------------|  
|MFCx0.DLL|DLL de MFC, versión de lanzamiento ANSI|  
|MFCx0U.DLL|DLL de MFC, versión de lanzamiento de Unicode|  
|Archivo MFCx0D.DLL|DLL de MFC, versión de depuración ANSI|  
|MFCx0UD.DLL|DLL de MFC, versión de depuración Unicode|  
  
 Si se vincula dinámicamente a la versión compartida del archivo DLL de MFC, ya sea desde una aplicación o desde un archivo DLL de extensión MFC, deberá incluir MFCx0.DLL con su producto. Si necesita compatibilidad con Unicode en la aplicación, incluya en su lugar MFCx0U.DLL.  
  
 Si el archivo DLL se vincula estáticamente a MFC, debe vincular con una de las bibliotecas MFC estáticas. Estas versiones se denominan según la convención de [N &#124; U] AFXCW [D]. LIB. Para obtener más información, vea la tabla "Convenciones de nomenclatura de biblioteca de vínculos estáticos" en [convenciones de nomenclatura de biblioteca](../mfc/library-naming-conventions.md) (MFC).  
  
 Para obtener una lista de archivos DLL de C++ Visual que se puede distribuir con las aplicaciones, vea Redist.txt en la instalación de Visual Studio.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [La convención de nomenclatura para las bibliotecas](../mfc/library-naming-conventions.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)