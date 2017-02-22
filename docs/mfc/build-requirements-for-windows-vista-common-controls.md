---
title: "Requisitos de compilaci&#243;n para los controles comunes de Windows Vista | Microsoft Docs"
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
  - "controles comunes (MFC)"
  - "controles comunes (MFC), requisitos de compilación"
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Requisitos de compilaci&#243;n para los controles comunes de Windows Vista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca de \(MFC\) de la clase de la base de Microsoft admite la versión 6.1 de Controles comunes de Windows.  Los controles comunes se incluyen en [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] y biblioteca se incluye en [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)].  La biblioteca proporciona nuevos métodos que mejoran las clases existentes, y las nuevas clases y métodos que los controles comunes de soporte de[!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)].  Cuando se compila la aplicación, debe seguir los requisitos de la compilación y de migración que se describen en las secciones siguientes.  
  
## Requisitos de la compilación  
  
### Versiones compatibles  
 Algunas nuevos métodos y clases solo admiten [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] y después, mientras que otros métodos también admiten sistemas operativos anteriores.  Una nota en la sección de `Requirements` de cada tema de método especifica cuando el sistema operativo mínimo es [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)].  
  
 Incluso si el equipo no se ejecuta [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)], puede compilar una aplicación MFC que se ejecuta en [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] si tiene los archivos de encabezado de MFC de la versión 6.1 del equipo.  Sin embargo, los controles comunes diseñados específicamente para [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] sólo funcionan en ese sistema, y omiten por sistemas operativos anteriores.  
  
### Juegos de caracteres compatibles  
 Los controles de común de Windows solo admiten el juego de caracteres Unicode, y no el juego de caracteres ANSI.  Si compila la aplicación en la línea de comandos, utilice ambos siguiente definen \(\/D\) las opciones del compilador para especificar Unicode como el juego de caracteres subyacente:  
  
```  
/D_UNICODE /DUNICODE  
```  
  
 Si compila la aplicación en el entorno de desarrollo integrado \(IDE\) de Visual Studio, especifique la opción de **Juego de caracteres Unicode** de la propiedad de **Juego de caracteres** en el nodo de **General** de propiedades de proyecto.  
  
 La versión ANSI de varios métodos de MFC ha sido starting desusada con la versión 6.1 de Controles comunes de Windows.  Para obtener más información, vea [API ANSI desusadas](../mfc/deprecated-ansi-apis.md).  
  
## Requisitos de migración  
 Si utiliza el IDE de Visual Studio para compilar una nueva aplicación MFC que utiliza la versión 6.1 de Controles comunes de Windows, el IDE automáticamente declara un adecuado manifiestos.  Sin embargo, si migra una aplicación MFC existente de una versión anterior de Visual Studio y desea utilizar los nuevos controles comunes, el IDE automáticamente no proporciona información de manifiesto para actualizar la aplicación.  En su lugar, debe insertar manualmente el código fuente siguiente en el archivo stdafx.h:  
  
```  
#ifdef UNICODE  
#if defined _M_IX86  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_IA64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_X64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#else  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#endif  
#endif  
```  
  
## Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)   
 [Gráfico de jerarquías](../mfc/hierarchy-chart.md)   
 [API ANSI desusadas](../mfc/deprecated-ansi-apis.md)