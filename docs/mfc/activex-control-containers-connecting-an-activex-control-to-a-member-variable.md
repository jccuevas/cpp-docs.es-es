---
title: "Contenedores de controles ActiveX: Conectar un control ActiveX a una variable de miembro | Microsoft Docs"
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
  - "contenedores de controles ActiveX [C++], obtener acceso a controles ActiveX"
  - "contenedores de controles ActiveX [C++], controles ActiveX como variables de miembro"
  - "controles ActiveX [C++], obtener acceso"
  - "controles ActiveX [C++], variables de miembro del proyecto"
  - "conectar controles ActiveX a variables de miembro del contenedor"
  - "variables miembro [C++], controles ActiveX del proyecto"
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenedores de controles ActiveX: Conectar un control ActiveX a una variable de miembro
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La manera más fácil de tener acceso a un control ActiveX dentro de la aplicación contenedora de control es asociar el control ActiveX con una variable miembro de la clase de diálogo que contendrá el control.  
  
> [!NOTE]
>  Ésta no es la única manera de tener acceso a un control incrustado dentro de una clase de contenedor, pero con el propósito de este artículo es suficiente.  
  
### Agregar una variable miembro a la clase de diálogo  
  
1.  En la vista de clases, haga clic con el botón secundario en la clase principal del diálogo para abrir el menú contextual.  Por ejemplo, `CContainerDlg`.  
  
2.  En el menú contextual, haga **Add** y de **Agregar variable**.  
  
3.  En el asistente para agregar variables miembro, haga clic en **Control variable**.  
  
4.  En el cuadro de lista de **Id. de control** , seleccione el identificador de control ActiveX incrustado.  Por ejemplo, `IDC_CIRCCTRL1`.  
  
5.  En el cuadro de **Nombre de la variable** , escriba un nombre.  
  
     Por ejemplo, `m_circctl`.  
  
6.  Haga clic en **Finalizar** para aceptar las opciones y salir del asistente para agregar variables miembro.  
  
## Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)