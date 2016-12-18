---
title: "Crear una aplicaci&#243;n de contenedor de documentos activo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores de documentos activos [C++], crear"
  - "documentos activos [C++], contenedores"
  - "aplicaciones [MFC], contenedor de documentos activos"
  - "contenedores [C++], documento activo"
  - "MFC COM [C++], contención de documentos activos"
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear una aplicaci&#243;n de contenedor de documentos activo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La manera más sencilla y recomendada de crear una aplicación contenedora de documentos activos es crear una aplicación contenedora de MFC EXE mediante el asistente para aplicaciones MFC, modifique la aplicación admita la contención del documento activo.  
  
#### Para crear una aplicación contenedora de documentos activos  
  
1.  En el menú de **archivo** , haga clic en **Project**en el submenú de **new** .  
  
2.  En el panel izquierdo, tipo de proyecto de **Visual C\+\+** en.  
  
3.  **Aplicación MFC** Seleccione en el panel derecho.  
  
4.  Asigne al proyecto `MyProj`, haga clic en **Aceptar**.  
  
5.  Seleccione la página de **Compatib. doc. compuestos** .  
  
6.  Seleccione la opción de **Contenedor** o de **Contenedor\/Completo\-Servidor** .  
  
7.  Active la casilla de **Contenedor de documentos activos** .  
  
8.  Haga clic en **Finalizar**.  
  
9. Cuando el asistente para aplicaciones MFC acaba de generar la aplicación, abra los siguientes archivos utilizando el explorador de soluciones:  
  
    -   MyProjview.cpp  
  
10. En MyProjview.cpp, realice los cambios siguientes:  
  
    -   En `CMyProjView::OnPreparePrinting`, reemplace el contenido de la función con el código siguiente:  
  
         [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/CPP/creating-an-active-document-container-application_1.cpp)]  
  
     `OnPreparePrinting` proporciona compatibilidad de impresión.  Este código reemplaza `DoPreparePrinting`, que es la preparación predeterminada de impresión.  
  
     Contención de documento activo proporciona un esquema que imprime mejorado:  
  
    -   Puede llamar primero al documento activo a través de su interfazde `IPrint`y indicarle que se imprima.  Esto es diferente de contención anterior OLE, en la que el contenedor tenía que generar una imagen del elemento contenido en el objeto de`CDC`de impresora.  
  
    -   Si da error, indican al elemento contenido que se imprima a través de su interfazde `IOleCommandTarget`  
  
    -   Si da error, crean posee la representación del elemento.  
  
     Las funciones estáticas `COleDocObjectItem::OnPrint` y `COleDocObjectItem::OnPreparePrinting`miembro, tal como se implementa en el código anterior, controle este esquema que imprime mejorado.  
  
11. Agregue cualquier implementación de dispone y compilar la aplicación.  
  
## Vea también  
 [Contención de documentos activos](../mfc/active-document-containment.md)