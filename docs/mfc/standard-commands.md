---
title: "Comandos est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "identificadores de comando, comandos estándar"
  - "comandos [C++], estándar"
  - "comandos estándar del menú Edición"
  - "menú Archivo"
  - "Ayuda, menús"
  - "identificadores [C++], identificadores de comando"
  - "comandos de OLE"
  - "identificadores definidos por programadores [C++]"
  - "identificadores de comandos estándar"
  - "comandos estándar"
  - "Comandos del menú Ver"
  - "Comandos del menú Ventana"
ms.assetid: 88cf3ab4-79b3-4ac6-9365-8ac561036fbf
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comandos est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El marco define muchos mensajes de comando estándar.  Los id. para estos comandos tienen normalmente el formulario:  
  
 **ID\_** *Source\_Item*  
  
 donde es *el origen* normalmente un nombre de menú y *un elemento* es un elemento de menú.  Por ejemplo, el identificador de comando para el comando de Nuevo en el menú archivo es `ID_FILE_NEW`.  Los id. de comando estándar se muestran en negrita en la documentación.  Los id. Programador\- definido se muestran en una fuente diferente de texto circundante.  
  
 A continuación se muestra una lista de algunos de los comandos más importantes compatibles:  
  
 *Comandos de menú archivo*  
 Nuevo, Abrir, cerrar, Save, Guardar como, configuración de página, configuración de impresión, imprimir, vista previa de impresión, salida, y archivos más\-reciente\- utilizados.  
  
 *Comandos de menú Edición*  
 La clear, Todo claro, copiar, cortar, búsqueda, pegar, repetición, reemplaza, seleccione Todo, deshacer, y rehacer.  
  
 *Comandos del menú Ver*  
 Barra de herramientas y de estado.  
  
 *Comandos del menú Ventana*  
 Nuevo, organice, cascada, mosaico Horizontal, mosaico Vertical, y división.  
  
 *Comandos del menú Ayuda*  
 Índice, Ayuda de Utilizar, y About.  
  
 *Comandos de OLE \(menú Edición\)*  
 Inserte el objeto New, edite los vínculos, el vínculo de pegar, el Pegado especial, y el objeto *typename* \(comandos de verbo\).  
  
 El marco de trabajo proporciona diversos niveles de compatibilidad para estos comandos.  Admiten algunos comandos solo mientras los id. definido del comando, mientras que otros se admiten con implementaciones completas.  Por ejemplo, el marco implementa el comando abierto en el menú archivo creando un nuevo objeto document, muestra un cuadro de diálogo abierto, y abra y lea el archivo.  En cambio, debe implementar comandos en el menú Edición personalmente, puesto que los comandos como **ID\_EDIT\_COPY** dependen de la naturaleza de los datos que se copian.  
  
 Para obtener más información sobre los comandos admitidos y de implementación proporcionado, vea [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md).  Definen los comandos de estándar en el archivo AFXRES.H.  
  
## Vea también  
 [Objetos de interfaz de usuario e identificadores de comando](../mfc/user-interface-objects-and-command-ids.md)