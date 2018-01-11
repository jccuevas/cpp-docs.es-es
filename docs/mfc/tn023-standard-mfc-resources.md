---
title: "TN023: Recursos de MFC estándar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.resources
dev_langs: C++
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6fded011fda52dfde46804b03699dc93469e5e32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn023-standard-mfc-resources"></a>TN023: Recursos de MFC estándar
Esta nota describe los recursos estándar proporcionada con y necesaria para la biblioteca MFC.  
  
## <a name="standard-resources"></a>Recursos estándar  
 MFC proporciona dos categorías de recursos predefinidos que puede usar en la aplicación: recursos de imágenes prediseñadas y recursos del marco estándar.  
  
 Recursos de imágenes prediseñadas son recursos adicionales que no dependen de la plataforma, pero que desea agregar a la interfaz de usuario de la aplicación. Los siguientes recursos de imágenes prediseñadas están incluidos en el ejemplo General de MFC [imágenes prediseñadas](../visual-cpp-samples.md):  
  
-   Common.rc: Un único archivo de recursos que contiene:  
  
    -   Una extensa colección de iconos que representan una variedad de tareas de procesamiento de datos y de trabajo.  
  
    -   Varios cursores comunes (Vea también Afxres.rc).  
  
    -   Un mapa de bits de barra de herramientas que contiene varios botones de barra de herramientas.  
  
    -   Los recursos de mapa de bits y el icono que se utilizan por Commdlg.dll.  
  
-   Indicate.rc: Contiene los recursos de cadena para los indicadores de estado de la tecla de barra de estado, como "Extremo" para las teclas BLOQ MAYÚS.  
  
-   Prompts.rc: Contiene los recursos de cadena de mensaje de menú para cada comando predefinido, como "Crear un nuevo documento" para `ID_FILE_NEW`.  
  
-   Commdlg.rc: Archivo de .rc compatible Visual C++ que contiene las plantillas de cuadro de diálogo COMMDLG estándar.  
  
 Recursos del marco estándar son recursos con identificadores definidos por el AFX que el marco de trabajo depende de las implementaciones internas. Rara vez necesitará cambiar estos recursos definidos por el AFX. Si lo hace, debe seguir el procedimiento descrito más adelante en este tema.  
  
 Los siguientes recursos de marco de trabajo se incluyen en el directorio MFC\INCLUDE:  
  
-   AFXRES.rc: Recursos comunes utilizados por el marco de trabajo.  
  
-   Afxprint.rc: Recursos específicos de impresión.  
  
-   AFXOLECL.rc: Recursos específicos de las aplicaciones de cliente OLE.  
  
-   Afxolev.rc: Recursos específicos de aplicaciones de servidor completas OLE.  
  
## <a name="using-clip-art-resources"></a>Uso de recursos de imágenes prediseñadas  
  
#### <a name="to-use-a-clip-art-binary-resource"></a>Para utilizar un recurso binario de imágenes prediseñadas  
  
1.  Abra el archivo de recursos de la aplicación en Visual C++.  
  
2.  Abra Common.rc. Este archivo contiene todos los recursos binarios prediseñadas. Esto puede tardar algún tiempo porque el archivo Common.rc se compila.  
  
3.  Mantenga presionada la tecla CTRL mientras arrastra los recursos que desea utilizar desde Common.rc al archivo de recursos de la aplicación.  
  
 Para usar otros recursos de imágenes prediseñadas, siga los mismos pasos. La única diferencia es que se abrirá el archivo .rc adecuado en lugar de Common.rc.  
  
> [!NOTE]
>  Tenga cuidado de no mover accidentalmente los recursos fuera de Common.rc permanentemente. Si mantiene la tecla CTRL mientras arrastra los recursos, se creará una copia. Si no presionado CTRL mientras arrastra, se moverán los recursos. Si le preocupa que podría accidentalmente realizados cambios en el archivo Common.rc, haga clic en "No" cuando se le pregunte si desea guardar los cambios en Common.rc.  
  
> [!NOTE]
>  Los archivos de recursos de .rc tienen una clase especial `TEXTINCLUDE` recursos en ellos que impedirán que se guarden accidentalmente encima de los archivos .rc estándar.  
  
### <a name="customizing-standard-framework-resources"></a>Personalizar recursos del marco estándar  
 Recursos del marco estándar se suelen incluir en una aplicación utilizando el #include comando en el archivo de recursos de la aplicación. AppWizard generará un archivo de recursos. Este archivo incluye los recursos de marco estándar adecuado, según las opciones de Asistente para aplicaciones que seleccione. Puede revisar, agregar o quitar los recursos que se incluyen cambiando las directivas de tiempo de compilación. Para ello, abra el **recursos** menú y seleccione **inclusión**. Vistazo "Directivas de tiempo de compilación" Editar elemento. Por ejemplo:  
  
```  
#include "afxres.rc"  
#include "afxprint.rc"  
```  
  
 Los casos más comunes de personalización de recursos del marco estándar consiste en Agregar o quitar adicional incluye para la impresión, OLE cliente y soporte técnico de servidor OLE.  
  
 En algunos casos excepcionales, que puede personalizar el contenido de los recursos del marco estándar para su aplicación concreta, no solo agregar y quitar todo el archivo. Los pasos siguientes muestran cómo puede limitar los recursos que se incluyen:  
  
##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>Para personalizar el contenido de un archivo de recursos estándar  
  
1.  Abra el archivo de recursos en Visual C++.  
  
2.  Con el comando de inclusión de recursos establecidos, quite el `#include` del archivo .rc estándar que desea personalizar. Por ejemplo, para personalizar la barra de herramientas de vista previa de impresión, quite el `#include "afxprint.rc"` línea.  
  
3.  Abra los archivos de recursos estándar adecuado en MFC\INCLUDE. Siguiendo el ejemplo anterior de este tema, el archivo adecuado es MFC\Include\Aafxprint.rc  
  
4.  Copie todos los recursos del archivo .rc estándar en el archivo de recursos de la aplicación.  
  
5.  Modificar la copia de los recursos estándar en el archivo de recursos de la aplicación.  
  
> [!NOTE]
>  No modifique los recursos directamente en los archivos .rc estándar. Si lo hace, modificará los recursos disponibles en todas las aplicaciones, no solo en el que se esté trabajando actualmente.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

