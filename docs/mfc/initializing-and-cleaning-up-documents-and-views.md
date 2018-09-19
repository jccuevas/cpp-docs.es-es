---
title: Inicializar y limpiar documentos y vistas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f59dcfbdac4a2d5da732c5e7f8cfc78083bf843
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346368"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Inicializar y limpiar documentos y vistas
Utilice las directrices siguientes para inicializar y limpiar después los documentos y vistas:  
  
-   El marco de trabajo MFC inicializa documentos y vistas; inicializar los datos que se les agrega.  
  
-   El marco de trabajo limpia como documentos y vistas de cierre; debe cancelar la asignación de memoria que asigna en el montón desde dentro de las funciones miembro de esos documentos y vistas.  
  
> [!NOTE]
>  Recuerde que la inicialización para toda la aplicación se realiza mejor en el reemplazo de la [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) función miembro de clase `CWinApp`, y limpieza para toda la aplicación se realiza mejor en el reemplazo de la `CWinApp`función miembro [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance).  
  
 El ciclo de vida de un documento (y su ventana de marco y la vista o vistas) en formularios MDI aplicación es como sigue:  
  
1.  Durante la creación dinámica, se llama al constructor del documento.  
  
2.  Para del cada nuevo documento, el documento [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) o [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) se llama.  
  
3.  El usuario interactúa con el documento a lo largo de su duración. Normalmente esto sucede mientras el usuario trabaja en los datos del documento a través de la vista, seleccionar y editar los datos. La vista pasa cambios en el documento para almacenar y actualizar otras vistas. Durante este período, el documento y la vista pueden controlar comandos.  
  
4.  Las llamadas de framework [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) para eliminar datos específicos de un documento.  
  
5.  Se llama el destructor del documento.  
  
 En una aplicación SDI, paso 1 se realiza una vez, cuando se crea el documento por primera vez. A continuación, en los pasos 2 a 4 se realizan varias veces cada vez que se abre un nuevo documento. El nuevo documento vuelve a utilizar el objeto de documento existente. Por último, paso 5 se realiza cuando finaliza la aplicación.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Inicialización de documentos y vistas](../mfc/initializing-documents-and-views.md)  
  
-   [Limpieza de documentos y vistas](../mfc/cleaning-up-documents-and-views.md)  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura documento/vista](../mfc/document-view-architecture.md)

