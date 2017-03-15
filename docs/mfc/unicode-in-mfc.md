---
title: "Unicode en MFC | Microsoft Docs"
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
  - "cadenas [C++], Unicode"
  - "Unicode [C++], habilitar"
  - "Unicode [C++], MFC"
  - "caracteres anchos, codificar"
  - "caracteres anchos, Unicode"
ms.assetid: 1002004b-4113-4380-bf63-e1570934b793
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Unicode en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC admite el estándar Unicode para codificar los caracteres anchos en las plataformas Windows NT, Windows 2000, y Windows XP.  Las aplicaciones de Unicode no pueden ejecutarse en las plataformas Windows 98.  
  
 Las versiones de Unicode de las bibliotecas MFC se describen a continuación:  
  
### Bibliotecas de vínculos estáticos  
  
|Release|Depurar|Descripción|  
|-------------|-------------|-----------------|  
|UAFXCW.lib, .pdb|UAFXCWD.lib, .pdb|Biblioteca de vínculos estáticos Unicode MFC|  
  
### Bibliotecas de vínculos dinámicos  
  
|Release|Depurar|Descripción|  
|-------------|-------------|-----------------|  
|MF C100 U.lib, .dbg, def, .dll, .map, .pdb, .prf|MF C100 UD.lib, .def, .dll, .map, .pdb|Biblioteca de importación Unicode MFC \(vea comentarios siguiente para la explicación de extensiones de archivo\)|  
|MF CS100 U.lib, .pdb|MF CS100 UD.lib, .pdb|Biblioteca de importación Unicode MFC que contiene código que se debe vincular estáticamente a una aplicación o DLL|  
  
 **Tipos de archivo**  
  
-   Los archivos de biblioteca de importación tienen la extensión \(.lib\).  
  
-   Los archivos de biblioteca de vínculos dinámicos tienen la extensión \(.dll\).  
  
-   Los archivos de definición de módulo \(.def\) son archivos de texto que contienen instrucciones para definir un archivo .exe o .dll.  
  
-   Los archivos de asignación \(.map\) son archivos de texto que contienen información que el vinculador utiliza al vincular un programa.  
  
-   Los archivos de biblioteca \(.lib\) se utilizan junto con las versiones de DLL de MFC.  Estos archivos contienen el código que se debe vincular estática en la aplicación o DLL.  
  
-   Los archivos de base de datos de programa \(.pdb\) contienen la depuración y la información de estado del proyecto.  
  
-   Los archivos de depuración \(.dbg\) contienen información \(COFF FPO, y CodeView\) que el depurador de Visual C\+\+ utiliza.  
  
 Para obtener información detallada sobre convenciones de nomenclatura, vea [Convenciones de nomenclatura para bibliotecas](../mfc/library-naming-conventions.md).  
  
 Para obtener información sobre cómo utilizar Unicode con MFC, vea [Cadenas: Unicode y compatibilidad con juegos de caracteres multibyte \(MBCS\)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
## Vea también  
 [Conceptos](../mfc/mfc-concepts.md)   
 [Temas generales de MFC](../mfc/general-mfc-topics.md)