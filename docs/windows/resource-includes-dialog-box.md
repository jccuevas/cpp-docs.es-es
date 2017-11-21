---
title: "Cuadro de diálogo de inclusión de recursos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.resourceincludes
dev_langs: C++
helpviewer_keywords:
- Resource Includes dialog box
- rc files, changing storage
- symbol header files, changing
- compiling source code, including resources
- .rc files, changing storage
- symbol header files, read-only
- symbols, symbol header files
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: be954451335deef88ad459b9de6b865ff45ed909
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="resource-includes-dialog-box"></a>Archivos de inclusión de recursos (cuadro de diálogo)
Puede usar el **incluye recursos** cuadro de diálogo Modificar hábito del entorno de almacenar todos los recursos en el archivo .rc del proyecto y todas las [símbolos](../windows/symbols-resource-identifiers.md) en Resource.h.  
  
 Para abrir el **incluye recursos** en el archivo de cuadro de diálogo, haga una .rc [vista de recursos](../windows/resource-view-window.md), a continuación, elija **incluye recursos** en el menú contextual.  
  
 **Archivo de encabezado de símbolos**  
 Permite cambiar el nombre del archivo de encabezado donde se almacenan las definiciones de los símbolos del archivo de recursos. Para obtener más información, consulte [cambiar los archivos de encabezado de nombres de símbolos](../windows/changing-the-names-of-symbol-header-files.md).  
  
 **Directivas de símbolos de solo lectura**  
 Permite incluir archivos de encabezado cuyos símbolos no deberían modificarse durante una sesión de edición. Por ejemplo, se puede incluir un archivo de símbolos compartido por varios proyectos. También se pueden incluir archivos .h de MFC. Para obtener más información, consulte [símbolos incluidos compartidos (de sólo lectura) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md).  
  
 **Directivas de tiempo de compilación**  
 Permite incluir archivos de recursos creados y editados con independencia de los recursos del archivo principal de recursos, con directivas de tiempo de compilación (como las que incluyen de forma condicional recursos) o con recursos en formato personalizado. Asimismo, el cuadro Directivas de tiempo de compilación puede usarse para incluir archivos de recursos de MFC estándar. Para obtener más información, consulte [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).  
  
> [!NOTE]
>  Las entradas de estos cuadros de texto aparecen en el archivo .rc marcadas por `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, y `TEXTINCLUDE 3` respectivamente. Para obtener más información, consulte [TN035: usar varios archivos de recursos y archivos de encabezado con Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).  
  
 Una vez que ha realizado cambios en el archivo de recursos mediante el **incluye recursos** cuadro de diálogo, debe cerrar el archivo .rc y vuelva a abrirlo para que surtan efecto los cambios. Para obtener más información, consulte [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).  
  

  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Cómo: especificar directorios de inclusión para recursos](../windows/how-to-specify-include-directories-for-resources.md)   
 [Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)   
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editores de recursos](../windows/resource-editors.md)