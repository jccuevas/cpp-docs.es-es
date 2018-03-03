---
title: Clases de plantillas de documentos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.document
dev_langs:
- C++
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbaccd12daf156d4a15f5cd18c31b5b230fe86db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="document-template-classes"></a>Clases de plantillas de documentos
Objetos de plantilla de documento coordinan la creación de documento, vista y objetos de ventana de marco cuando un documento nuevo o se crea la vista.  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md)  
 La clase base para plantillas de documento. No se utiliza esta clase nunca directamente; en su lugar, use una de las otras clases de plantilla de documento derivadas de esta clase.  
  
 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)  
 Una plantilla para los documentos en la interfaz de múltiples documentos (MDI). Las aplicaciones MDI pueden tener varios documentos abiertos a la vez.  
  
 [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)  
 Una plantilla para los documentos en la interfaz de único documento (SDI). SDI (aplicaciones) tienen sólo un documento abierto a la vez.  
  
## <a name="related-class"></a>Clase relacionada  
 [CCreateContext](../mfc/reference/ccreatecontext-structure.md)  
 Una estructura pasada por una plantilla de documento a las funciones de creación de la ventana para coordinar la creación de objetos de documento, vista y ventana de marco.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

