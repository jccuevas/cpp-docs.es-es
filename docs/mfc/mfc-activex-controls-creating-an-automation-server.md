---
title: "Controles ActiveX MFC: Crear un servidor de automatizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], servidor de automatización"
  - "servidores de automatización [C++], controles ActiveX en MFC"
  - "controles ActiveX en MFC [C++], servidor de automatización"
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Controles ActiveX MFC: Crear un servidor de automatizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede desarrollar un control ActiveX de MFC como servidor de automatización con el propósito mediante programación de insertar que control en otros métodos de aplicación y del control de la aplicación.  Tal control todavía estaría disponible hospedarse en un contenedor de controles ActiveX.  
  
### Para crear un control como servidor de automatización  
  
1.  [crear](../mfc/reference/mfc-activex-control-wizard.md) el control.  
  
2.  [Agregue los métodos](../mfc/mfc-activex-controls-methods.md).  
  
3.  Reemplazo [IsInvokeAllowed](../Topic/COleControl::IsInvokeAllowed.md).  Para obtener más información, vea el artículo Q146120 de Knowledge Base.  
  
4.  Crear el control.  
  
### Para tener acceso mediante programación a los métodos en un servidor de automatización  
  
1.  Cree una aplicación, por ejemplo, [MFC EXE](../mfc/reference/mfc-application-wizard.md).  
  
2.  Al principio de la función de `InitInstance` , agregue la línea siguiente:  
  
     [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/CPP/mfc-activex-controls-creating-an-automation-server_1.cpp)]  
  
3.  En la vista de clases, haga clic con el botón secundario en el proyecto y **Add class from typelib** seleccione para importar la biblioteca de tipos.  
  
     Esto agregará los archivos con extensiones de nombre de archivo .h y .cpp al proyecto.  
  
4.  En el archivo de encabezado de la clase donde se llamará a uno o más métodos del control ActiveX, agregue la línea siguiente: `#include filename.h`, donde el nombre del archivo de encabezado que se creó al importar la biblioteca de tipos.  
  
5.  En la función donde una llamada se lleve a un método en el control ActiveX, agregue el código que crea un objeto de la clase contenedora de control y cree el objeto ActiveX.  Por ejemplo, el siguiente código MFC crea instancias de un control de `CCirc` , obtiene la propiedad caption, y muestra el resultado cuando el botón ACEPTAR se hace clic en un cuadro de diálogo:  
  
     [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/CPP/mfc-activex-controls-creating-an-automation-server_2.cpp)]  
  
 Si agrega métodos al control ActiveX después de que se utiliza en una aplicación, puede usar la última versión del control en la aplicación eliminar archivos creados al importar la biblioteca de tipos.  A continuación importa la biblioteca de tipos de nuevo.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)