---
title: "Archivos HTML | Microsoft Docs"
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
  - "asistentes personalizados, HTML (archivos)"
  - "asistentes personalizados, interfaz de usuario"
  - "archivos [C++], creado mediante un asistente personalizado"
  - "páginas HTML, interfaz de usuario para asistentes personalizados"
  - "interfaz de usuario para asistentes"
  - "asistentes [C++], interfaz de usuario para asistentes personalizados"
ms.assetid: 3b6ed080-6560-418b-b908-d84d71bdf145
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Archivos HTML
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un asistente puede contener una interfaz de usuario de tipo HTML.  Además del archivo Default.htm, el asistente puede contener un número indeterminado de archivos .htm que se pueden especificar en el cuadro **Número de páginas** del [Asistente personalizado](../ide/custom-wizard.md).  Cada archivo .htm representa una página HTML del asistente a la que se tiene acceso con los botones **Siguiente** y **Atrás**, mediante fichas o con cualquier otro formato que especifique en el diseño del asistente.  
  
 Cada archivo HTML contiene:  
  
-   La etiqueta SYMBOL, que identifica los valores predeterminados de las opciones definidas por el usuario.  Los símbolos se escriben en la tabla de símbolos cuando el usuario hace clic en **Finalizar**, por ejemplo:  
  
```  
<SYMBOL NAME='HEADER_FILE' VALUE='MyHeader.h' TYPE=text></SYMBOL>  
```  
  
 En la interfaz de usuario del asistente, el cuadro de texto identificado en la tabla de símbolos como "HEADER\_FILE" contiene el texto predeterminado "MyHeader.h".  Este valor de la interfaz de usuario del asistente puede cambiarse; el valor resultante se escribirá en la tabla de símbolos del proyecto al hacer clic en **Finalizar**, por ejemplo:  
  
```  
<SYMBOL NAME='CHECKBOX1' TYPE=checkbox VALUE=false></SYMBOL>  
```  
  
 En la interfaz de usuario del asistente, la casilla identificada en la tabla de símbolos como "CHECKBOX1" estará desactivada de forma predeterminada.  No obstante, es posible activarla en la interfaz de usuario HTML; el valor resultante se escribirá en la tabla de símbolos al hacer clic en **Finalizar**.  
  
 Todos los archivos .htm registran las selecciones del usuario en la tabla de símbolos.  
  
-   Una inclusión para Default.js y [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md), archivo que contiene las funciones de JScript más útiles y habituales.  
  
-   Referencias a las imágenes del proyecto que han de aparecer en el archivo HTML.  
  
-   Texto HTML y formato para personalizar el aspecto de la interfaz de usuario del asistente.  
  
-   Funciones de JScript con las que se obtiene acceso al Modelo de objetos para asistentes de Visual C\+\+ con el fin de ofrecer un comportamiento personalizado desde el propio asistente.  Estas funciones se encuentran en la sección de la página HTML con el encabezado \<SCRIPT LANGUAGE\='JSCRIPT'\>, como se muestra en el ejemplo recogido a continuación.  
  
    > [!NOTE]
    >  Para obtener acceso al Asistente y a los Modelos de objetos de entorno desde HTML, anteponga "window.external" al elemento del modelo de objetos.  
  
    ```  
    function InitDocument(document)  
    {  
       setDirection();  
  
       if (window.external.FindSymbol('DOCUMENT_FIRST_LOAD'))  
       {  
          // This function sets the default symbols based   
          // on the values specified in the SYMBOL tags above  
          //  
          window.external.SetDefaults(document);  
       }  
  
       // Load the document and initialize the controls   
       // with the appropriate symbol values  
       //  
       window.external.Load(document);  
    }  
    ```  
  
 A continuación, se muestra un ejemplo de asistente para aplicaciones de consola:  
  
```  
<SYMBOL NAME='WIZARD_DIALOG_TITLE' TYPE=text VALUE='Console Application Wizard'></SYMBOL>  
  
<SYMBOL NAME='EMPTY_PROJECT' TYPE=checkbox VALUE=false></SYMBOL>  
<SYMBOL NAME='SUPPORT_ATL' TYPE=checkbox VALUE=false></SYMBOL>  
<SYMBOL NAME='SUPPORT_MFC' TYPE=checkbox VALUE=false></SYMBOL>  
```  
  
## Vea también  
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)