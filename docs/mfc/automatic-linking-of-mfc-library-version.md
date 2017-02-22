---
title: "Vinculaci&#243;n autom&#225;tica de la versi&#243;n de la biblioteca MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "defaultlib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vínculos automáticos [C++]"
  - "defaultlib en MFC"
  - "vincular [C++]"
  - "vincular [C++], automáticamente de la versión de la biblioteca MFC"
  - "vincular [C++], de MFC"
  - "MFC (bibliotecas), vincular a"
  - "MFC (bibliotecas), versiones"
ms.assetid: 02af4a20-2034-4fce-b200-c2202c3c8311
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Vinculaci&#243;n autom&#225;tica de la versi&#243;n de la biblioteca MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En versiones de MFC antes de la versión 3.0 \(antes de la versión 2.0 de Visual C\+\+\), tendrá que especificar manualmente la versión correcta de la biblioteca MFC en la lista de entrada de bibliotecas para el vinculador.  Con la versión 3.0 de MFC y versiones posteriores, ya no es necesario especificar manualmente la versión de la biblioteca MFC.  En su lugar, los archivos de encabezado de MFC determinan automáticamente la versión correcta de la biblioteca MFC, dependiendo de los valores definidos con `#define`, como **\_DEBUG** o **\_UNICODE**.  Los archivos de encabezado de MFC agregan directivas de **\/defaultlib** que indican al vinculador para vincular una versión específica de la biblioteca MFC.  
  
 Por ejemplo, el fragmento de código siguiente del archivo de encabezado AFX.H indica al vinculador para vincular en la versión de NAFXCWD.LIB o de NAFXCW.LIB de MFC, dependiendo de si utiliza la versión de depuración de MFC:  
  
 `#ifndef _UNICODE`  
  
 `#ifdef _DEBUG`  
  
 `#pragma comment(lib, "nafxcwd.lib")`  
  
 `#else`  
  
 `#pragma comment(lib, "nafxcw.lib")`  
  
 `#endif`  
  
 `#else`  
  
 `#ifdef _DEBUG`  
  
 `#pragma comment(lib, "uafxcwd.lib")`  
  
 `#else`  
  
 `#pragma comment(lib, "uafxcw.lib")`  
  
 `#endif`  
  
 `#endif`  
  
 Los archivos de encabezado de MFC también vinculadas en todas las bibliotecas necesarias, incluidas las bibliotecas MFC, bibliotecas de Win32, bibliotecas OLE, bibliotecas compiladas de ejemplos, bibliotecas OLE ODBC, etc.  Las bibliotecas de Win32 incluyen Kernel32.Lib, User32.Lib, y GDI32.Lib.  
  
## Vea también  
 [Versiones de la biblioteca MFC](../mfc/mfc-library-versions.md)