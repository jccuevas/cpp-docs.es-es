---
title: Crear una aplicación de contenedor de documentos activo
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
ms.openlocfilehash: 860a8531a96a0671c808dba13523b492026eafe0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616350"
---
# <a name="creating-an-active-document-container-application"></a>Crear una aplicación de contenedor de documentos activo

La forma más sencilla y recomendada de crear una aplicación contenedora de documentos activa es crear una aplicación contenedora EXE de MFC mediante el Asistente para aplicaciones MFC y, a continuación, modificar la aplicación para admitir la contención de documentos activos.

#### <a name="to-create-an-active-document-container-application"></a>Para crear una aplicación de contenedor de documentos activos

1. En el menú **archivo** , haga clic en **proyecto**en el submenú **nuevo** .

1. En el panel izquierdo, haga clic en **Visual C++** tipo de proyecto.

1. Seleccione **aplicación MFC** en el panel derecho.

1. Asigne al proyecto el nombre *MyProj*y haga clic en **Aceptar**.

1. Seleccione la página **compatibilidad con documentos compuestos** .

1. Seleccione la opción **contenedor** o **contenedor/servidor completo** .

1. Active la casilla **contenedor de documentos activos** .

1. Haga clic en **Finalizar**

1. Cuando el Asistente para aplicaciones MFC termine de generar la aplicación, abra los siguientes archivos mediante Explorador de soluciones:

   - *MyProjview. cpp*

1. En *MyProjview. cpp*, realice los cambios siguientes:

   - En `CMyProjView::OnPreparePrinting` , reemplace el contenido de la función por el código siguiente:

     [!code-cpp[NVC_MFCDocView#56](codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting`proporciona compatibilidad con la impresión. Este código reemplaza a `DoPreparePrinting` , que es la preparación de impresión predeterminada.

   La contención de documentos activos proporciona un esquema de impresión mejorado:

   - En primer lugar, puede llamar al documento activo a través de su `IPrint` interfaz e indicar que se imprima. Esto es diferente de la contención de OLE anterior, en la que el contenedor tenía que representar una imagen del elemento contenido en el objeto de impresora `CDC` .

   - Si se produce un error, indique al elemento contenido que se imprima a través de su `IOleCommandTarget` interfaz.

   - Si se produce un error, cree su propia representación del elemento.

   Las funciones miembro estáticas `COleDocObjectItem::OnPrint` y `COleDocObjectItem::OnPreparePrinting` , tal y como se implementa en el código anterior, controlan este esquema de impresión mejorado.

1. Agregue cualquier implementación de su propia y compile la aplicación.

## <a name="see-also"></a>Consulte también

[Contención de documentos activos](active-document-containment.md)
