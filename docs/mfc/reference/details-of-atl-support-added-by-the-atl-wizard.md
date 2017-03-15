---
title: "Informaci&#243;n detallada sobre la compatibilidad agregada por el Asistente para ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.atl.support"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, MFC (proyectos)"
  - "MFC, compatibilidad ATL"
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Informaci&#243;n detallada sobre la compatibilidad agregada por el Asistente para ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Al [agregar compatibilidad ATL a un ejecutable o DLL MFC existentes](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual C\+\+ hace las siguientes modificaciones en el proyecto MFC existente \(en este ejemplo, el proyecto se denomina `MFCEXE`\):  
  
-   Se agregan dos nuevos archivos \(un archivo .idl y un archivo .rgs, usado para registrar el servidor\).  
  
-   En los archivos principales de encabezado e implementación \(Mfcexe.h y Mfcexe.cpp\) se agrega una nueva clase \(derivada de **CAtlMFCModule**\).  Además de la nueva clase, se agrega código de registro a `InitInstance`.  También se agrega código a la función `ExitInstance` con el fin de revocar el objeto de clase.  En el archivo de encabezado, por último, se incluyen dos nuevos archivos de encabezado \(Initguid.h y Mfcexe\_i.c\) en el archivo de implementación, declarando e inicializando los nuevos GUID para la clase derivada de **CAtlMFCModule**.  
  
-   Con objeto de registrar el servidor adecuadamente, se agrega una entrada para el nuevo archivo .rgs al archivo de recursos del proyecto.  
  
## Notas para los proyectos de DLL  
 Al agregar compatibilidad ATL a un proyecto DLL MFC, se podrán apreciar ciertas diferencias:  Se agrega código a las funciones **DLLRegisterServer** y **DLLUnregisterServer** para registrar o anular el registro de la DLL.  También se agrega código a [DllCanUnloadNow](../Topic/CAtlDllModuleT::DllCanUnloadNow.md) y [DllGetClassObject](../Topic/CAtlDllModuleT::DllGetClassObject.md).  
  
## Vea también  
 [Compatibilidad con ATL en un proyecto MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)   
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Explorar la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)