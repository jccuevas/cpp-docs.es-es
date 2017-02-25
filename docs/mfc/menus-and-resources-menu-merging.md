---
title: "Men&#250;s y recursos: Combinaci&#243;n de men&#250;s | Microsoft Docs"
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
  - "coordinar diseños de menú"
  - "menús [C++], aplicaciones de documentos OLE"
  - "combinar barra de herramientas y barra de estado"
  - "contenedores OLE, menús y recursos"
  - "barras de estado, aplicaciones de documentos OLE"
  - "barras de herramientas [C++], aplicaciones de documentos OLE"
  - "edición visual, menús y recursos de la aplicación"
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Men&#250;s y recursos: Combinaci&#243;n de men&#250;s
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Detalles del artículo los pasos necesarios para que las aplicaciones VIEJAS de documento administran la edición y la activación en contexto visuales correctamente.  La activación de contexto supone un desafío para las aplicaciones del contenedor y del servidor \(componente\).  El usuario permanece en la misma ventana de marco \(en el contexto del documento contenedor\) pero se ejecuta realmente otra aplicación \(el servidor\).  Esto requiere la coordinación entre los recursos del contenedor y las aplicaciones de servidor.  
  
 Temas cubiertos en incluyen de caso:  
  
-   [Diseños de menú](#_core_menu_layouts)  
  
-   [Barras de herramientas y barras de estado](#_core_toolbars_and_status_bars)  
  
##  <a name="_core_menu_layouts"></a> Diseños de menú  
 El primer paso es coordinar diseños de menú.  Para obtener más información, vea la sección de **Menu Creation** en [Consideraciones de programación del menú](https://msdn.microsoft.com/en-us/library/ms647557.aspx) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 Las aplicaciones contenedoras debe crear un nuevo menú que se utilizará cuando los elementos incrustados se provocan en contexto.  En el mínimo, este menú debe ser el siguiente, en el orden indicado:  
  
1.  Menú archivo idéntico al que se utiliza cuando los archivos abiertos. \(No se coloca normalmente ningún otro elementos de menú antes del siguiente elemento.\)  
  
2.  Dos separadores consecutivos.  
  
3.  Menú Ventana idéntico al que se utiliza cuando los archivos abiertos \(solo si la aplicación contenedora en una aplicación MDI\).  Algunas aplicaciones pueden tener otros menús, como un menú de opciones, que pertenecen a este grupo, que permanecen en el menú cuando un elemento incrustado se provoca en contexto.  
  
    > [!NOTE]
    >  Puede haber otros menús que afectan a la vista del documento contenedor, como zoom.  Los menús de contenedor aparecen entre los dos separadores en este recurso de menú.  
  
 Las aplicaciones de Servidor \(componente\) también deben crear un nuevo menú específicamente para la activación en contexto.  Debe estar como menú utilizado cuando los archivos abiertos, pero sin los elementos de menú, como archivo y ventana que manipulan el documento de servidor en lugar de los datos.  Normalmente, este menú consta de lo siguiente:  
  
1.  Menú Edición idéntico al que se utiliza cuando los archivos abiertos.  
  
2.  Separador.  
  
3.  Objeto que edita menús, tales como el menú del lápiz en la aplicación de ejemplo scribble.  
  
4.  Separador.  
  
5.  Menú ayuda.  
  
 Para obtener un ejemplo, consulte el diseño de algunos menús en contexto de ejemplo para un contenedor y un servidor.  Los detalles de cada elemento de menú se han quitado para crear el del ejemplo.  El menú en el contexto del contenedor tiene las siguientes entradas:  
  
```  
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE   
BEGIN  
    POPUP "&File C1"  
    MENUITEM SEPARATOR  
    POPUP "&Zoom C2"  
    MENUITEM SEPARATOR  
    POPUP "&Options C3"  
    POPUP "&Window C3"  
END  
```  
  
 Los separadores consecutivos indican que la primera parte del menú de servidor debe ir.  Ahora busque el menú en el contexto del servidor:  
  
```  
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE   
BEGIN  
    POPUP "&Edit S1"  
    MENUITEM SEPARATOR  
    POPUP "&Format S2"  
    MENUITEM SEPARATOR  
    POPUP "&Help S3"  
END  
```  
  
 Los separadores aquí indican que el segundo grupo de elementos de menú de contenedor debe ir.  La estructura de menú resultante cuando un objeto de este servidor es en el lugar se produce dentro de este contenedor tiene el siguiente aspecto:  
  
```  
BEGIN  
    POPUP "&File C1"  
    POPUP "&Edit S1"  
    POPUP "&Zoom C2"  
    POPUP "&Format S2"  
    POPUP "&Options C3  
    POPUP "&Window C3"  
    POPUP "&Help S3"  
END  
```  
  
 Como puede ver, separadores se han reemplazado con varios grupos de menú de cada aplicación.  
  
 Las tablas de aceleradores asociadas al menú de contexto también se deben proporcionar por la aplicación de servidor.  El contenedor las incorporará en sus propias tablas de aceleradores.  
  
 Cuando un elemento incrustado se genera en su lugar, el marco de trabajo carga el menú en contexto.  Pida a la aplicación de servidor para el menú activación in situ y la inserta donde los separadores.  Así es cómo los menús combinan.  Se obtiene menús de contenedor para trabajar en la posición del archivo y la ventana, y se obtiene menús de servidor para trabajar en el elemento.  
  
##  <a name="_core_toolbars_and_status_bars"></a> Barras de herramientas y barras de estado  
 Las aplicaciones de servidor deben crear una barra de herramientas nueva y almacenar el mapa de bits en un archivo independiente.  Las aplicaciones asistente\- generadas aplicación almacena este mapa de bits en un archivo denominado ITOOLBAR.BMP.  La nueva barra de herramientas reemplaza la barra de herramientas de la aplicación contenedora cuando el elemento del servidor se provoca en contexto, y debe contener los mismos elementos que la barra de herramientas normal, pero quita los iconos que representan elementos del archivo y menús Ventana.  
  
 Esta barra de herramientas se carga en `COleIPFrameWnd`\- clase derivada, creará automáticamente por el asistente para aplicaciones.  La barra de estado controla la aplicación contenedora.  Para obtener más información sobre la implementación de las ventanas de contexto de cuadro, vea [Servidores: Implementar en un Servidor](../mfc/servers-implementing-a-server.md).  
  
## Vea también  
 [Menús y recursos \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [Activación](../mfc/activation-cpp.md)   
 [Servidores](../mfc/servers.md)   
 [Contenedores](../mfc/containers.md)