---
title: "Menu Command Properties | Microsoft Docs"
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
  - "menu items, properties"
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Menu Command Properties
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La información siguiente se organiza según las propiedades de menú que aparecen en la [ventana Propiedades](../Topic/Properties%20Window.md) al seleccionar un comando de menú. Aparecen ordenadas alfabéticamente, aunque en la ventana también se pueden ordenar por categoría.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|**Break**|Puede ser uno de estos valores:<br /><br /> -   **None** \(predeterminado\): sin interrupción.<br />-   **Column**: en los menús estáticos, este valor sitúa el comando de menú en una nueva línea. En los menús emergentes, este valor sitúa el comando de menú en una columna nueva, sin línea divisoria entre las columnas. Esta propiedad solo afecta a la apariencia del menú en tiempo de ejecución, no en el editor de menús.<br />-   **Bar**: igual que Column, con la excepción de que, en los menús emergentes, este valor separa la nueva columna de la antigua con una línea vertical. Esta propiedad solo afecta a la apariencia del menú en tiempo de ejecución, no en el editor de menús.|  
|**Título**|El texto que etiqueta el comando de menú \(el nombre del menú\). Para convertir una de las letras del título de un comando de menú en la tecla de acceso, sitúe delante de ella una Y comercial \(&\).|  
|**Activadas**|Si es True, el comando de menú se inicia en un primer momento. Tipo: booleano. Valor predeterminado: False.|  
|**Habilitado**|Si es **False**, se deshabilita el elemento de menú.|  
|**Grayed**|Si es True, el comando de menú se atenúa y se encuentra inactivo en un primer momento. Tipo: booleano. Valor predeterminado: False.|  
|**Ayuda**|Alinea el elemento de menú a la derecha. Por ejemplo, el comando de menú **Ayuda** siempre está a la derecha en todas las aplicaciones de Windows. Si establece esta propiedad en un elemento de menú, ese elemento aparecerá en el extremo derecho y al final del menú. Se aplica a los elementos de nivel superior. Valor predeterminado: **False**.|  
|**Id.**|Un símbolo definido en el archivo de encabezado. Tipo: símbolo, entero o cadena entrecomillada. Puede usar cualquier símbolo de los que se encuentran disponibles normalmente en cualquier editor, aunque la [ventana Propiedades](../Topic/Properties%20Window.md) no proporciona ninguna lista desplegable donde seleccionar.|  
|**Popup**|Si es True, el comando de menú es un menú emergente. Tipo: booleano. Valor predeterminado: True para los menús de nivel superior en una barra de menús. En caso contrario, es False.|  
|**Preguntar**|Contiene el texto que aparece en la barra de estado cuando se resalta el comando de menú. El texto se sitúa en la tabla de cadenas con el mismo identificador que el comando de menú. Esta propiedad se encuentra disponible para cualquier tipo de proyecto, pero la funcionalidad en tiempo de ejecución es específica de MFC.|  
|**Right to Left Justify**|Justifica a la derecha el comando de menú en la barra de menús, en tiempo de ejecución. Tipo: booleano. Valor predeterminado: False.|  
|**Right to Left Order**|Permite mostrar los comandos de menú de derecha a izquierda cuando la interfaz se localiza a idiomas con esta dirección de lectura, como el hebreo o el árabe.|  
|**Separador**|Si es True, el comando de menú es un separador. Tipo: booleano. Valor predeterminado: False.|  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Menu Editor](../mfc/menu-editor.md)