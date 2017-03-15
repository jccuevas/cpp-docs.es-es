---
title: "TN023: Recursos de MFC est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.resources"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "recursos [MFC]"
  - "recursos estándar"
  - "TN023"
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# TN023: Recursos de MFC est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota describe los recursos estándar proporcionados y necesarios para la biblioteca MFC.  
  
## Recursos estándar  
 MFC proporciona dos categorías de recursos predefinidos que puede utilizar en la aplicación: recursos de imágenes prediseñadas y recursos estándar de .NET framework.  
  
 Recursos de imágenes prediseñadas son recursos adicionales que no depende del marco de, pero que puede agregar a la interfaz de usuario de la aplicación.  Contienen los siguientes recursos de imágenes prediseñadas en el ejemplo [CLIPART](../top/visual-cpp-samples.md)MFC General:  
  
-   Common.rc: Un único archivo de recursos que contiene:  
  
    -   Una colección grande de iconos que representan una variedad de negocio y tareas de procesamiento de datos.  
  
    -   Varios cursores comunes \(vea también Afxres.rc\).  
  
    -   Un mapa de bits de la barra de herramientas que contiene varios botones de la barra de herramientas.  
  
    -   Los recursos del mapa de bits y el icono utilizados por Commdlg.dll.  
  
-   Indicate.rc: Contiene recursos de cadena de los marcadores de la tecla\- provincia de barra de estado, como “CAPITAL” para BLOQ MAYÚS.  
  
-   Prompts.rc: Contiene los recursos de cadena de menú\- mensaje para cada comando predefinido, por ejemplo “crear un nuevo documento” para `ID_FILE_NEW`.  
  
-   Commdlg.rc: Un archivo compatible de Visual C\+\+ .rc que contiene las plantillas de diálogo estándar de COMMDLG.  
  
 Los recursos estándar de marco son recursos con id. AFX\- definido que el marco depende de para las implementaciones internas.  Necesitará raramente cambiar estos recursos AFX\- definido.  Si lo hace, debe realizar el procedimiento explica más adelante en este tema.  
  
 Contienen los siguientes recursos de.NET framework del directorio de MFC\\INCLUDE:  
  
-   Afxres.rc: Recursos comunes utilizados por el marco.  
  
-   Afxprint.rc: Recursos específicos para imprimir.  
  
-   Afxolecl.rc: Recursos específicos de las aplicaciones cliente OLE.  
  
-   Afxolev.rc: Recursos específicos de las aplicaciones de servidor OLE completas.  
  
## Uso de recursos de imágenes prediseñadas  
  
#### Para utilizar un recurso binario de imágenes prediseñadas  
  
1.  Abra el archivo de recursos de la aplicación en Visual C\+\+.  
  
2.  Common.rc abierto.  Este archivo contiene todos los recursos binarios de imágenes prediseñadas.  Esto puede tardar algún tiempo porque se compila el archivo de Common.rc.  
  
3.  Mantenga presionada la tecla CTRL mientras se arrastra a los recursos que desee utilizar de Common.rc al archivo de recursos de la aplicación.  
  
 Para utilizar otros recursos de imágenes prediseñadas, siga los mismos pasos.  La única diferencia es que se abrirá el archivo adecuado .rc en lugar de Common.rc.  
  
> [!NOTE]
>  Tenga cuidado de no mover involuntariamente recursos de Common.rc permanentemente.  Si mantiene presionada la tecla CTRL mientras se arrastra a recursos, se crea una copia.  Si no subject CTRL abajo mientras de arrastre, los recursos moverá.  Si le preocupa que haya realizado accidentalmente cambios en el archivo de Common.rc, haga clic en “no” cuando se le pregunte si desea guardar los cambios en Common.rc.  
  
> [!NOTE]
>  Los archivos de recursos .rc tienen un recurso especial de `TEXTINCLUDE` en ellos que impiden que se guarde accidentalmente encima de los archivos del estándar .rc.  
  
### Personalizar los recursos estándar de .NET framework  
 Incluyen los recursos estándar de marco normalmente en una aplicación utilizando el comando \#include en el archivo de recursos de una aplicación.  AppWizard generará un archivo de recursos.  Este archivo incluye recursos de estándar adecuada, dependiendo de las opciones de AppWizard selecciona.  Puede revisar, agregar, quitar o cambiar incluyen a qué recursos las directivas en tiempo de compilación.  Para ello, abra el menú de **Recurso** y seleccione **El conjunto incluye**.  Busque el elemento de edición “las directivas en tiempo de compilación”.  Por ejemplo:  
  
```  
#include "afxres.rc"  
#include "afxprint.rc"  
```  
  
 El caso más habitual de personalizar los recursos estándar de .NET framework está agregando o el quitar adicional incluye para la compatibilidad de cliente que imprime, OLE, y servidor OLE.  
  
 En algunos casos raros se puede personalizar el contenido de los recursos estándar de .NET framework para la aplicación determinada, no solo para agregar y quitar el archivo completo.  Los pasos de los siguiente muestran cómo puede restringir los recursos a los que se incluyen:  
  
##### Para personalizar el contenido de un archivo de recursos estándar  
  
1.  Abra el archivo de recursos en Visual C\+\+.  
  
2.  Mediante el comando concreto de Inclusión de recursos, quite `#include` para el archivo standard .rc que desea personalizar.  Por ejemplo, para personalizar la barra de herramientas de la vista previa de impresión, quite la línea de `#include "afxprint.rc"` .  
  
3.  Abra los archivos de recursos estándar de adecuada en MFC\\INCLUDE.  Después del ejemplo anterior de este tema, el archivo adecuado es MFC\\Include\\Aafxprint.rc  
  
4.  Copie todos los recursos de archivo estándar de .rc al archivo de recursos de la aplicación.  
  
5.  Modifique la copia de los recursos estándar en el archivo de recursos de la aplicación.  
  
> [!NOTE]
>  No modifique los recursos directamente en los archivos del estándar .rc.  Al hacerlo se modificará los recursos disponibles en cada aplicación, no solo en la que está trabajando actualmente.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)