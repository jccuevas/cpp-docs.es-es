---
title: "Agregar compatibilidad con ATL a un proyecto MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.adding.atl.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, MFC (proyectos)"
  - "MFC, compatibilidad ATL"
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Agregar compatibilidad con ATL a un proyecto MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Si ya creó una aplicación basada en MFC, puede agregar compatibilidad con la biblioteca ATL \(Active Template Library\) fácilmente, ejecutando el asistente Agregar compatibilidad ATL a MFC.  
  
> [!NOTE]
>  ATL y MFC no se admiten normalmente en las ediciones Express de Visual Studio.  
  
> [!NOTE]
>  Esta compatibilidad sólo se aplica a los objetos COM simples agregados a un ejecutable MFC o un proyecto de DLL.  Se pueden agregar otros objetos COM \(incluidos control ActiveX\) a proyectos MFC, pero es posible que los objetos no funcionen según lo esperado.  
  
### Para agregar compatibilidad ATL a un proyecto MFC  
  
1.  En el Explorador de soluciones, haga clic con el botón secundario en el proyecto al que desee agregar compatibilidad con ATL.  
  
2.  En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar clase**.  
  
3.  Seleccione el icono **Agregar compatibilidad ATL a un proyecto MFC**.  
  
    > [!NOTE]
    >  Este icono se encuentra en la carpeta ATL, en el panel **Categorías**.  
  
4.  Cuando se le pida, haga clic en **Sí** para agregar compatibilidad con ATL.  
  
 Para obtener más información sobre cómo afecta al código de su proyecto MFC agregar compatibilidad con ATL, vea [Información detallada sobre la compatibilidad agregada por el Asistente para ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)  
  
## Vea también  
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Explorar la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)