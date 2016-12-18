---
title: "Versiones de AFXDLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "afxdll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "biblioteca AFXDLL"
  - "asistentes para aplicaciones [C++], usos predeterminados de AFXDLL"
  - "versión del archivo DLL de MFC [C++]"
  - "MFC [C++], versión de AFXDLL"
  - "DLL de MFC [C++], vinculación dinámica a biblioteca"
  - "bibliotecas MFC [C++], vinculación dinámica"
ms.assetid: c078ae8f-85a9-43cb-9ded-c09ca2c45723
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Versiones de AFXDLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En lugar de compilar la aplicación vincular estáticamente a bibliotecas de código objeto MFC, puede compilar la aplicación para utilizar una de las bibliotecas de AFXDLL, que contienen MFC en un archivo DLL que ejecutar aplicaciones múltiples pueden compartir.  Para una tabla de nombres AFXDLL, vea [Archivos DLL: Convenciones de nomenclatura](../build/naming-conventions-for-mfc-dlls.md).  
  
> [!NOTE]
>  De forma predeterminada, el asistente para aplicaciones MFC crea un proyecto de EN.  Para utilizar la vinculación estática de código MFC en su lugar, establezca la opción de **Utilizar MFC en una biblioteca estática** en el asistente para aplicaciones MFC.  Vinculación estática no está disponible en Standard Edition de Visual C\+\+.  
  
## Vea también  
 [Versiones de la biblioteca MFC](../mfc/mfc-library-versions.md)