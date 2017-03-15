---
title: "Archivos DLL que no est&#225;n basados en MFC: informaci&#243;n general | Microsoft Docs"
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
  - "DLL [C++], no basada en MFC"
  - "DLL no basada en MFC [C++]"
ms.assetid: 1ed5d1ee-e20c-47d7-801d-87ea26a73842
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Archivos DLL que no est&#225;n basados en MFC: informaci&#243;n general
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los archivos DLL que no están basados en MFC no utilizan internamente las funciones de MFC y las funciones que se exportan de los mismos podrán llamarse desde archivos ejecutables basados o no en MFC.  Las funciones se suelen exportar desde un archivo DLL no basado en MFC mediante la interfaz estándar de C.  
  
 Para obtener más información acerca de los archivos DLL que no están basados en MFC, vea [Bibliotecas de vínculos dinámicos](http://msdn.microsoft.com/library/windows/desktop/ms682589) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  
  
## ¿Qué desea hacer?  
  
-   [Crear un archivo DLL para Win32](../Topic/How%20to:%20Create%20a%20Windows%20Desktop%20Application.md)  
  
-   [Exportar de un archivo DLL](../build/exporting-from-a-dll.md)  
  
-   [Vincular un ejecutable a un archivo DLL](../build/linking-an-executable-to-a-dll.md)  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Archivos DLL estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Archivos DLL de extensión: información general](../build/extension-dlls-overview.md)  
  
## Vea también  
 [Tipos de archivos DLL](../build/kinds-of-dlls.md)