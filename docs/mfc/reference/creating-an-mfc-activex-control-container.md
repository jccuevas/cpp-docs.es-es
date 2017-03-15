---
title: "Crear un contenedor de controles ActiveX MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.activex.container"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores de controles ActiveX [C++], crear"
  - "contenedores [C++], crear"
  - "controles ActiveX en MFC [C++], contenedores"
  - "controles OLE [C++], contenedores"
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Crear un contenedor de controles ActiveX MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un contenedor de controles ActiveX es un programa primario que proporciona el entorno necesario para que puedan ejecutarse controles ActiveX \(antes denominados controles OLE\).  Para crear una aplicación que pueda contener controles ActiveX puede utilizar MFC y puede no utilizarlo; pero es mucho más fácil crear la aplicación con MFC.  
  
 Si crea un programa contenedor MFC mediante el [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md), podrá tener acceso a las distintas características de los controles ActiveX y a la Automatización que implementan MFC y las clases ActiveX.  Entre estas características están incluidas la edición visual, la Automatización, la creación de archivos compuestos y la compatibilidad con controles.  Entre las opciones de edición visual \(proporcionadas por el Asistente para aplicaciones MFC\) compatibles con el programa primario están la creación de un contenedor, un miniservidor, un servidor completo y un programa que actúe a la vez como contenedor y como servidor.  
  
-   **Aplicación MFC nueva**.  Para crear un programa MFC nuevo que incluya Automatización, edición visual, archivos compuestos o compatibilidad con controles, utilice el Asistente para aplicaciones MFC y elija las opciones de automatización apropiadas.  
  
-   **Aplicación MFC existente**.  Si desea agregar la capacidad de contener controles a una aplicación MFC existente, vea [Contenedores de controles ActiveX: habilitar manualmente la contención de controles ACtiveX](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md).  
  
### Puede crear un contenedor ActiveX para los tipos de aplicaciones siguientes  
  
1.  [Contenedores](../../mfc/containers.md)  
  
2.  [Edición visual](../../mfc/ole-mfc.md)  
  
3.  [Controles ActiveX MFC](../../mfc/mfc-activex-controls.md)  
  
## Vea también  
 [Tipos de proyecto de Visual C\+\+](../../ide/visual-cpp-project-types.md)