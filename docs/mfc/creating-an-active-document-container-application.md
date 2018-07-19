---
title: Crear una aplicación de contenedor de documentos activo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8817133ba1004e746f568ad3e039de5130693174
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929450"
---
# <a name="creating-an-active-document-container-application"></a>Crear una aplicación de contenedor de documentos activo
La forma más sencilla y más recomendada para crear una aplicación de contenedor de documentos activo consiste en crear una aplicación de contenedor de EXE de MFC mediante el Asistente para aplicaciones MFC, a continuación, modifique la aplicación para soportar la contención de documentos activos.  
  
#### <a name="to-create-an-active-document-container-application"></a>Para crear una aplicación de contenedor de documentos activos  
  
1.  Desde el **archivo** menú, haga clic en **proyecto**desde el **New** submenú.  
  
2.  En el panel izquierdo, haga clic en **Visual C++** tipo de proyecto.  
  
3.  Seleccione **aplicación MFC** en el panel derecho.  
  
4.  Denomine el proyecto *MyProj*, haga clic en **Aceptar**.  
  
5.  Seleccione el **compatibilidad con documentos compuestos** página.  
  
6.  Seleccione el **contenedor** o **contenedor o servidor completo** opción.  
  
7.  Seleccione el **contenedor de documentos activos** casilla de verificación.  
  
8.  Haga clic en **Finalizar**.  
  
9. Cuando el Asistente para aplicaciones MFC termina de generar la aplicación, abra los archivos siguientes con el Explorador de soluciones:  
  
    -   *Archivo MyProjview.cpp*  
  
10. En *archivo MyProjview.cpp*, realice los cambios siguientes:  
  
    -   En `CMyProjView::OnPreparePrinting`, reemplace el contenido de la función con el código siguiente:  
  
         [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]  
  
     `OnPreparePrinting` proporciona compatibilidad con la impresión. Este código reemplaza `DoPreparePrinting`, que es la preparación de impresión predeterminada.  
  
     Contención de documentos activos proporciona un esquema de impresión mejorado:  
  
    -   Puede llamar primero al documento activo a través de su `IPrint` interfaz y le indique que se imprima. Esto es diferente de contención OLE anterior, en el que el contenedor tenía que procesar una imagen del elemento contenido en la impresora `CDC` objeto.  
  
    -   Si eso no funciona, indique al elemento contenido que se imprima a través de su `IOleCommandTarget` (interfaz)  
  
    -   Si se produce un error, asegúrese de su propia representación del elemento.  
  
     Las funciones miembro estáticas `COleDocObjectItem::OnPrint` y `COleDocObjectItem::OnPreparePrinting`, tal y como se implementa en el código anterior, controlar este esquema de impresión mejorado.  
  
11. Agregue sus propias implementaciones y compile la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Contención de documentos activos](../mfc/active-document-containment.md)

