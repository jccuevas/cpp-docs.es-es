---
title: "Clases y funciones generadas por el Asistente para archivos DLL de MFC | Microsoft Docs"
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
  - "clases [C++], generado mediante el asistente para archivos DLL de MFC"
  - "código [C++], generado mediante el asistente para archivos DLL de MFC"
  - "DLL [C++], clases y funciones de asistente"
  - "funciones [MFC]"
  - "funciones [MFC], DLL"
  - "Asistente para archivos DLL de MFC"
ms.assetid: e69e62fe-4953-42bf-a2fc-50bbf9bdaeaf
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Clases y funciones generadas por el Asistente para archivos DLL de MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El código que genera el Asistente para archivos DLL de MFC dependerá del tipo de archivo DLL que esté creando y de las opciones que haya seleccionado.  El Asistente para archivos DLL de MFC genera el mismo código para las dos formas de archivos DLL.  
  
|Tipo de archivo DLL|Opción|Clases|Funciones|  
|-------------------------|------------|------------|---------------|  
|[Extensión](../../build/extension-dlls-overview.md)|None|None|`DllMain`|  
|[Estándar](../../build/regular-dlls-dynamically-linked-to-mfc.md)|None|Clase de aplicación derivada de `CWinApp`|None|  
|[Estándar](../../build/regular-dlls-dynamically-linked-to-mfc.md)|Automatización|Clase de aplicación derivada de `CWinApp`|**DllGetClassObjectDllCanUnloadNowDllRegisterServer**|  
|[Extensión](../../build/extension-dlls-overview.md)|Windows Sockets|None|`DllMain`|  
|[Estándar](../../build/regular-dlls-dynamically-linked-to-mfc.md)|Windows Sockets|Clase de aplicación derivada de `CWinApp`|`InitInstance` contiene una llamada a `AfxSocketInit`|  
  
## Vea también  
 [Asistente para archivos DLL de MFC](../../mfc/reference/mfc-dll-wizard.md)