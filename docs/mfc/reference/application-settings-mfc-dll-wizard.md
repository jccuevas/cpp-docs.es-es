---
title: "Configuraci&#243;n de la aplicaci&#243;n, Asistente para archivos DLL de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.dll.appset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para archivos DLL de MFC, configuración de la aplicación"
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Configuraci&#243;n de la aplicaci&#243;n, Asistente para archivos DLL de MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilice esta página del Asistente para archivos DLL de MFC para diseñar y agregar características básicas a un nuevo proyecto DLL de MFC.  
  
## Tipo de archivo DLL  
 Seleccione el tipo de archivo DLL que desee crear.  
  
 **Archivo DLL estándar que utiliza el archivo DLL compartido de MFC**  
 Seleccione esta opción para vincular la biblioteca MFC al programa como un archivo DLL compartido.  Con esta opción, no puede compartir objetos MFC entre el archivo DLL y la aplicación que llama.  El programa hace llamadas a la biblioteca MFC en tiempo de ejecución.  Esta opción reduce los requisitos de disco y memoria del programa si éste está formado por varios archivos ejecutables que utilizan la biblioteca MFC.  Tanto Win32 como los programas MFC pueden llamar a las funciones del archivo DLL.  Debe redistribuir el archivo DLL de MFC con este tipo de proyecto.  
  
 **Archivo DLL estándar con MFC vinculada estáticamente**  
 Seleccione esta opción para vincular estáticamente el programa a la biblioteca MFC en tiempo de compilación.  Tanto Win32 como los programas MFC pueden llamar a las funciones del archivo DLL.  Aunque esta opción aumenta el tamaño del programa, no tiene que redistribuir el archivo DLL de MFC con este tipo de proyecto.  No puede compartir objetos MFC entre el archivo DLL y la aplicación que llama.  
  
 **DLL de extensión MFC**  
 Seleccione esta opción si desea que el programa realice llamadas a la biblioteca MFC en tiempo de ejecución y si desea compartir objetos MFC entre el archivo DLL y la aplicación que llama.  Esta opción reduce los requisitos de disco y memoria del programa si éste está compuesto de varios archivos ejecutables que utilizan la biblioteca MFC.  Sólo los programas MFC podrán llamar a las funciones del archivo DLL.  Debe redistribuir el archivo DLL de MFC con este tipo de proyecto.  
  
## Características adicionales  
 Puede elegir que el archivo DLL de MFC sea compatible con la automatización o con Windows sockets.  
  
 **Automatización**  
 Seleccione **Automatización** para permitir al programa manipular objetos implementados en otro programa.  Al seleccionar **Automatización** también expone el programa a otros clientes de automatización.  Vea [Automatización](../../mfc/automation.md) para obtener más información.  
  
 **Windows sockets**  
 Seleccione esta opción para indicar que el programa es compatible con Windows sockets.  Windows sockets permite escribir programas que se comuniquen a través de redes TCP\/IP.  
  
 Cuando se crea el archivo DLL de MFC con compatibilidad con Windows sockets, [CWinApp::InitInstance](../Topic/CWinApp::InitInstance.md) inicializa dicha compatibilidad con los sockets y el archivo de encabezado MFC StdAfx.h incluye AfxSock.h.  
  
## Vea también  
 [Asistente para archivos DLL de MFC](../../mfc/reference/mfc-dll-wizard.md)   
 [Crear un proyecto DLL de MFC](../../mfc/reference/creating-an-mfc-dll-project.md)