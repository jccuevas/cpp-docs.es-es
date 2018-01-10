---
title: "Cómo: convertir una cinta MFC existente a un recurso de cinta de opciones | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7cb0d5d80edd52a85834963d030e35eef96d718
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Cómo: Convertir una cinta de MFC existente en un recurso de cinta
Recursos de la cinta de opciones son más fáciles de visualizar, modificar y mantener que las cintas de opciones codificada de forma manual. En este tema se describe cómo convertir una cinta de opciones codificada de forma manual en un proyecto MFC en un recurso de cinta de opciones.  
  
 Debe tener un proyecto MFC existente que tiene código que utiliza las clases de la cinta de opciones MFC, por ejemplo, [CMFCRibbonBar (clase)](../mfc/reference/cmfcribbonbar-class.md).  
  
### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>Para convertir una cinta de MFC en un recurso de cinta  
  
1.  En Visual Studio, en un proyecto MFC existente, abra el archivo de origen donde se inicializa el objeto CMFCRibbonBar. Normalmente, el archivo es mainfrm.cpp. Agregue el código siguiente después del código de inicialización de la cinta de opciones.  
  
 ```  
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");

 ```  
  
     Guarde y cierre el archivo.  
  
2.  Compilar y ejecutar la aplicación MFC y, a continuación, en el Bloc de notas, abra RibbonOutput.txt y copie su contenido.  
  
3.  En Visual Studio, en el **proyecto** menú, haga clic en **Agregar recurso**. En el **Agregar recurso** cuadro de diálogo, seleccione **cinta** y, a continuación, haga clic en **nuevo**.  
  
     Visual Studio crea un recurso de cinta y lo abre en la vista Diseño. El identificador de recurso de cinta es IDR_RIBBON1, que se muestra en **vista de recursos**. La cinta de opciones se define en el archivo XML de ms ribbon1.mfcribbon.  
  
4.  En Visual Studio, abra ribbon1.mfcribbon-ms, elimine su contenido y, a continuación, pegue el contenido de RibbonOutput.txt, que copió anteriormente. Guarde y cierre ms ribbon1.mfcribbon.  
  
5.  Volver a abrir el archivo de origen donde se inicializa el objeto CMFCRibbonBar (normalmente, mainfrm.cpp) y marque como comentario existente código de la cinta de opciones. Agregue el código siguiente después del código que convirtió en comentario.  
  
 ```  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);

 ```  
  
6.  Compile el proyecto y ejecutar el programa.  
  
## <a name="see-also"></a>Vea también  
 [Diseñador de la cinta de opciones (MFC)](../mfc/ribbon-designer-mfc.md)

