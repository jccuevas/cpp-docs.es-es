---
title: "Consejos sobre programación con MBCS general | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mbcs
dev_langs: C++
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 2136f017e177cea80f6832f7c1b9ba4e2d843bcf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="general-mbcs-programming-advice"></a>Consejos generales sobre la programación con MBCS
Utilice las siguientes sugerencias:  
  
-   Para obtener flexibilidad, usar macros de tiempo de ejecución como `_tcschr` y `_tcscpy` siempre que sea posible. Para obtener más información, consulte [asignaciones de texto genérico en Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Utilice el tiempo de ejecución de C `_getmbcp` función para obtener información acerca de la página de códigos actual.  
  
-   No reutilice los recursos de cadena. Dependiendo del lenguaje de destino, una cadena determinada podría tener un significado diferente cuando se traduce. Por ejemplo, menú principal de "Archivo" en la aplicación podría traducir de forma diferente de la cadena "File" en un cuadro de diálogo. Si necesita utilizar más de una cadena con el mismo nombre, utilice identificadores diferentes para cada uno.  
  
-   Puede averiguar si la aplicación se está ejecutando en un sistema operativo habilitado para MBCS. Para ello, establezca una marca al inicio del programa; No confíe en las llamadas de API.  
  
-   Al diseñar cuadros de diálogo, deje aproximadamente un 30% espacio adicional al final de los controles de texto estático para la conversión de MBCS.  
  
-   Tenga cuidado al seleccionar fuentes para la aplicación, ya que algunas fuentes no están disponibles en todos los sistemas. Por ejemplo, la versión en japonés de Windows 2000 no admite la fuente Helvetica.  
  
-   Al seleccionar la fuente para los cuadros de diálogo, utilice [MS Shell Dlg](http://msdn.microsoft.com/library/windows/desktop/dd374112) en lugar de MS Sans Serif o Helvetica. MS Shell Dlg se reemplaza por la fuente correcta por el sistema antes de crear el cuadro de diálogo. El uso de MS Shell Dlg garantiza que los cambios en el sistema operativo para tratar con esta fuente estarán disponibles automáticamente. (MFC reemplaza MS Shell Dlg por DEFAULT_GUI_FONT o la fuente del sistema en Windows 95, Windows 98 y Windows NT 4 porque estos sistemas no controlan MS Shell Dlg correctamente.)  
  
-   Al diseñar la aplicación, decidir las cadenas que se pueden localizar. En caso de duda, suponga que una cadena determinada se localizará. Por lo tanto, no mezcle cadenas que se pueden localizar con las que no.  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)   
 [Aumento y disminución de punteros](../text/incrementing-and-decrementing-pointers.md)