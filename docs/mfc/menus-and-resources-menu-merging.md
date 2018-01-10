---
title: "Menús y recursos: combinación de menús | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c686d461a3052feb4a55cf7948b58102f10ac1f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="menus-and-resources-menu-merging"></a>Menús y recursos: Combinación de menús
En este artículo se detalla los pasos necesarios para aplicaciones de documentos OLE controlar la edición visual y la activación en contexto correctamente. Activación en contexto supone un desafío para el contenedor y servidor de aplicaciones (componente). El usuario permanece en la misma ventana de marco (dentro del contexto del documento contenedor), pero está realmente se está ejecutando otra aplicación (el servidor). Esto requiere la coordinación entre los recursos de las aplicaciones de contenedor y servidor.  
  
 Los temas tratados en este artículo son:  
  
- [Diseños de menús](#_core_menu_layouts)  
  
- [Barras de herramientas y barras de estado](#_core_toolbars_and_status_bars)  
  
##  <a name="_core_menu_layouts"></a>Diseños de menús  
 El primer paso es coordinar diseños de menús. Para obtener más información, consulte el **menú creación** sección [consideraciones sobre la programación de menú](https://msdn.microsoft.com/library/ms647557.aspx) del SDK de Windows.  
  
 Aplicaciones de contenedor deben crear un nuevo menú para usarse solo cuando se activan los elementos incrustados en su lugar. Como mínimo, este menú debe constar de los siguientes valores, en el orden indicado:  
  
1.  Menú archivo idéntico al utilizado cuando hay archivos abiertos. (Normalmente no hay otros elementos de menú se colocan delante del siguiente elemento.)  
  
2.  Dos separadores consecutivos.  
  
3.  Menú Ventana idéntico al utilizado cuando hay archivos abiertos (solo si la aplicación contenedora en una aplicación MDI). Algunas aplicaciones pueden tener otros menús, por ejemplo, un menú de opciones, que pertenecen a este grupo, que permanece en el menú cuando se activa un elemento incrustado en su lugar.  
  
    > [!NOTE]
    >  Puede haber otros menús que afectan a la vista del documento contenedor, como Zoom. Estos menús del contenedor se muestran entre los dos separadores de este recurso de menú.  
  
 Las aplicaciones de servidor (componente) también deben crear un nuevo menú específicamente para la activación en contexto. Debe ser como el menú que se utiliza cuando hay archivos abiertos, pero sin elementos de menú, como archivo y ventana, que manipulan el documento del servidor en lugar de los datos. Normalmente, este menú consta de las siguientes acciones:  
  
1.  Un menú Edición idéntico al utilizado cuando hay archivos abiertos.  
  
2.  Separador.  
  
3.  Objeto de menús, por ejemplo, el menú de lápiz en la aplicación de ejemplo de Scribble de edición.  
  
4.  Separador.  
  
5.  Menú de ayuda.  
  
 Para obtener un ejemplo, examine el diseño de algunos menús en lugar de ejemplo para un contenedor y un servidor. Se han quitado los detalles de cada elemento de menú para que el ejemplo más claro. Menús de in situ del contenedor tiene las siguientes entradas:  
  
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
  
 Los separadores consecutivos indican dónde debe colocarse la primera parte del menú del servidor. Ahora examinemos menús de in situ del servidor:  
  
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
  
 Los separadores indican dónde debe colocarse el segundo grupo de elementos de menú del contenedor. La estructura de menús resultante cuando se activa un objeto de este servidor en su lugar dentro de este contenedor tiene el siguiente aspecto:  
  
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
  
 Como puede ver, se han reemplazado los separadores por los diferentes grupos de cada menú de la aplicación.  
  
 Asociado con el menú en lugar de tablas de aceleradores también deben proporcionarse por la aplicación de servidor. El contenedor incorporará a sus propias tablas de aceleradores.  
  
 Cuando se activa un elemento incrustado en su lugar, el marco de trabajo carga el menú contextual. A continuación, se pide a la aplicación de servidor para el menú para la activación en contexto y se inserta donde están los separadores. Se trata cómo se combinan los menús. Obtener los menús del contenedor para el funcionamiento en la ubicación del archivo y ventana, y recibirá menús desde el servidor para el funcionamiento en el elemento.  
  
##  <a name="_core_toolbars_and_status_bars"></a>Barras de herramientas y barras de estado  
 Las aplicaciones de servidor deben crear una nueva barra de herramientas y almacenar su mapa de bits en un archivo independiente. Las aplicaciones de aplicación generados por el Asistente almacenan este mapa de bits en un archivo denominado ITOOLBAR. BMP. La nueva barra de herramientas reemplaza la barra de herramientas de la aplicación contenedora cuando el elemento del servidor se activa en su lugar y debe contener los mismos elementos que la barra de herramientas normal, pero quitar iconos que representan los elementos de los menús archivo y ventana.  
  
 Esta barra de herramientas se carga en su `COleIPFrameWnd`-clase derivada, creada automáticamente el Asistente para aplicaciones. La barra de estado se controla mediante la aplicación contenedora. Para obtener más información sobre la implementación de ventanas de marco en contexto, vea [servidores: implementar un servidor](../mfc/servers-implementing-a-server.md).  
  
## <a name="see-also"></a>Vea también  
 [Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)   
 [Activación](../mfc/activation-cpp.md)   
 [Servidores](../mfc/servers.md)   
 [Contenedores](../mfc/containers.md)

