---
title: Uso de documentos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], C++ applications
- data [MFC], reading
- documents [MFC]
- files [MFC], writing to
- data [MFC], documents
- files [MFC]
- views [MFC], C++ applications
- document/view architecture [MFC], documents
- reading data [MFC], documents and views
- printing [MFC], documents
- writing to files [MFC]
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 691d8d00b9c4671ea4b9c318313851a7fab73f7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-documents"></a>Usar documentos
En colaboración, documentos y vistas:  
  
-   Contener, administrar y mostrar su específica de la aplicación [datos](../mfc/managing-data-with-document-data-variables.md).  
  
-   Proporcionar una interfaz que consta de [variables de datos de documentos](../mfc/managing-data-with-document-data-variables.md) para manipular los datos.  
  
-   Participar en [escribir y leer archivos](../mfc/serializing-data-to-and-from-files.md).  
  
-   Participar en [impresión](../mfc/role-of-the-view-in-printing.md).  
  
-   [Controlar](../mfc/handling-commands-in-the-document.md) la mayoría de los comandos y mensajes de la aplicación.  
  
 El documento está especialmente implicado en la administración de datos. Almacenar los datos, normalmente, en variables de miembro de clase de documento. La vista utiliza estas variables para tener acceso a los datos para su presentación y actualizar. Mecanismo de serialización predeterminado del documento administra la lectura y escritura de los datos en y desde archivos. Documentos también pueden controlar comandos (pero distinto de los mensajes de Windows no **WM_COMMAND**).  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Derivar una clase de documento de CDocument](../mfc/deriving-a-document-class-from-cdocument.md)  
  
-   [Administrar datos con variables de datos de documento](../mfc/managing-data-with-document-data-variables.md)  
  
-   [Serializar datos en y desde archivos](../mfc/serializing-data-to-and-from-files.md)  
  
-   [Omitir el mecanismo de serialización](../mfc/bypassing-the-serialization-mechanism.md)  
  
-   [Controlar comandos en el documento](../mfc/handling-commands-in-the-document.md)  
  
-   [Función miembro OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)  
  
-   [Función miembro DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura documento/vista](../mfc/document-view-architecture.md)

