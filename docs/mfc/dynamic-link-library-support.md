---
title: "Compatibilidad con la biblioteca de v&#237;nculos din&#225;micos | Microsoft Docs"
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
  - "DLL [C++], MFC"
  - "DLL de MFC [C++], archivos DLL estándar"
  - "NAFXDW.LIB"
  - "NAFXDWD.LIB"
  - "DLL estándar [C++], proyecto destinado como DLL"
  - "USRDLL, compatibilidad con DLL"
ms.assetid: cc31c69f-3c78-4db1-9ecd-0fd8dc3217e3
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compatibilidad con la biblioteca de v&#237;nculos din&#225;micos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las bibliotecas de NAFXCW.lib y de NAFXCWD.lib \(enumeradas en la tabla de convenciones de nomenclatura para bibliotecas de vínculos estáticos en [Convenciones de nomenclatura para bibliotecas](../mfc/library-naming-conventions.md)\) crean el proyecto como una biblioteca de vínculos dinámicos, denominado “archivo DLL estándar” \(antes un “USRDLL”\) que se puede utilizar con las aplicaciones no compiladas con la biblioteca de clases.  Esta compatibilidad de DLL no es lo mismo que MFCx0.DLL y MFCx0D.DLL \(denominados AFXDLL\), que contienen la biblioteca de clases completa del archivo DLL.  Para obtener más información, vea [DLLs](../build/dlls-in-visual-cpp.md).  Para una tabla de nombres del archivo DLL, vea [Convenciones de nomenclatura para archivos DLL de MFC](../build/naming-conventions-for-mfc-dlls.md).  
  
## Vea también  
 [Versiones de la biblioteca MFC](../mfc/mfc-library-versions.md)