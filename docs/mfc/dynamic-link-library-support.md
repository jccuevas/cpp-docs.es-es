---
title: "Compatibilidad con bibliotecas de vínculos dinámicos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- regular MFC DLLs [MFC], project targets as DLLs
- DLLs [MFC], MFC
- NAFXDW.LIB
- MFC DLLs [MFC], regular MFC DLLs
- USRDLLs, DLL support
- NAFXDWD.LIB
ms.assetid: cc31c69f-3c78-4db1-9ecd-0fd8dc3217e3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 95e7586dc15c641ff4915b3257f4ed33a552fde2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="dynamic-link-library-support"></a>Compatibilidad con la biblioteca de vínculos dinámicos
Las bibliotecas NAFXCW.lib y NAFXCWD.lib (enumeradas en la tabla de convenciones de nomenclatura de biblioteca de vínculos estáticos de [convenciones de nomenclatura de biblioteca](../mfc/library-naming-conventions.md)) crear el proyecto como una biblioteca de vínculos dinámicos, denominada una "DLL de MFC normal" (antiguamente un "archivo USRDLL") que se puede utilizar con aplicaciones no generadas con la biblioteca de clases. Esta compatibilidad DLL no es lo mismo que MFCx0.DLL y MFCx0D.DLL (conocida como AFXDLL), que contiene la biblioteca de clases completa en un archivo DLL. Para obtener más información, consulte [dll](../build/dlls-in-visual-cpp.md). Para una tabla de nombres de archivos DLL, consulte [convenciones de nomenclatura para archivos DLL de MFC](../build/naming-conventions-for-mfc-dlls.md).  
  
## <a name="see-also"></a>Vea también  
 [Versiones de la biblioteca MFC](../mfc/mfc-library-versions.md)

