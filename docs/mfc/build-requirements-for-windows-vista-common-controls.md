---
title: "Requisitos de compilación para controles comunes de Windows Vista | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- common controls (MFC), build requirements
- common controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a6f6dabd14ddb95f1b4c2b49389c27f61a69970f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="build-requirements-for-windows-vista-common-controls"></a>Requisitos de compilación para los controles comunes de Windows Vista
La biblioteca (Microsoft Foundation Classes) admite la versión 6.1 de controles comunes de Windows. Los controles comunes se incluyen en [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] y la biblioteca se incluye en el [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]. La biblioteca proporciona nuevos métodos que mejoran las clases existentes y nuevas clases y métodos que admiten [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] controles comunes. Cuando se compila la aplicación, debe cumplir los requisitos de compilación y la migración que se describen en las secciones siguientes.  
  
## <a name="compilation-requirements"></a>Requisitos de compilación  
  
### <a name="supported-versions"></a>Versiones admitidas  
 Algunas nuevas clases y métodos solamente es compatible con [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] y versiones posteriores, mientras que otros métodos también admiten los sistemas operativos anteriores. Una nota en la `Requirements` sección de cada tema de método especifica cuando la mínima necesaria es de sistema operativo [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)].  
  
 Incluso si el equipo no se ejecuta [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)], puede crear una aplicación MFC que se ejecutará en [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] si tiene los archivos de encabezado MFC versión 6.1 en el equipo. Sin embargo, que están diseñadas específicamente para controles comunes de [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] funcionan únicamente en el sistema y omite los sistemas operativos anteriores.  
  
### <a name="supported-character-sets"></a>Juegos de caracteres compatibles  
 Los nuevos controles comunes de Windows admiten solo el juego de caracteres Unicode y no el juego de caracteres ANSI. Si compila la aplicación en la línea de comandos, usar ambos de la definición siguiente (/ d.) juego de caracteres de opciones del compilador para especificar Unicode como subyacente:  
  
```  
/D_UNICODE /DUNICODE  
```  
  
 Si compila la aplicación en el entorno de desarrollo integrado (IDE) de Visual Studio, especifique la **juego de caracteres Unicode** opción de la **del juego de caracteres** propiedad en la **General**  nodo de las propiedades del proyecto.  
  
 La versión ANSI de varios métodos MFC se han quedado obsoletas a partir de controles comunes de Windows versión 6.1. Para obtener más información, consulte [en desuso API ANSI](../mfc/deprecated-ansi-apis.md).  
  
## <a name="migration-requirements"></a>Requisitos de migración  
 Si utiliza el IDE de Visual Studio para crear una nueva aplicación MFC que utiliza la versión 6.1 de controles comunes de Windows, el IDE declara automáticamente un manifiesto adecuado. Sin embargo, si migra una aplicación MFC existente desde una versión anterior de Visual Studio y desea utilizar los nuevos controles comunes, el IDE no proporciona automáticamente información del manifiesto para actualizar la aplicación. En su lugar, debe insertar manualmente el siguiente código fuente en el archivo stdafx.h:  
  
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
  
## <a name="see-also"></a>Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)   
 [Gráfico de jerarquías](../mfc/hierarchy-chart.md)   
 [API ANSI en desuso](../mfc/deprecated-ansi-apis.md)

