---
title: "Propiedades de comando de menú | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- menu items, properties
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 186790db57c20abf9f67f693ff60029257ebd4f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="menu-command-properties"></a>Propiedades de los comandos de menú
La información siguiente se organiza según las propiedades de menú que aparecen en la [ventana Propiedades](/visualstudio/ide/reference/properties-window) al seleccionar un comando de menú. Aparecen ordenadas alfabéticamente, aunque en la ventana también se pueden ordenar por categoría.  
  
|Property|Descripción|  
|--------------|-----------------|  
|**Break**|Puede ser uno de estos valores:<br /><br /> -   **Ninguno** (predeterminado): sin interrupción.<br />-   **Column**: en los menús estáticos, este valor sitúa el comando de menú en una nueva línea. En los menús emergentes, este valor sitúa el comando de menú en una columna nueva, sin línea divisoria entre las columnas. Esta propiedad solo afecta a la apariencia del menú en tiempo de ejecución, no en el editor de menús.<br />-   **Bar**: igual que Column, con la excepción de que, en los menús emergentes, este valor separa la nueva columna de la antigua con una línea vertical. Esta propiedad solo afecta a la apariencia del menú en tiempo de ejecución, no en el editor de menús.|  
|**Título**|El texto que etiqueta el comando de menú (el nombre del menú). Para convertir una de las letras del título de un comando de menú en la tecla de acceso, sitúe delante de ella una Y comercial (&).|  
|**Activadas**|Si es True, el comando de menú se inicia en un primer momento. Tipo: booleano. Valor predeterminado: False.|  
|**Habilitado**|Si es **False**, se deshabilita el elemento de menú.|  
|**Grayed**|Si es True, el comando de menú se atenúa y se encuentra inactivo en un primer momento. Tipo: booleano. Valor predeterminado: False.|  
|**Ayuda**|Alinea el elemento de menú a la derecha. Por ejemplo, el comando de menú **Ayuda** siempre está a la derecha en todas las aplicaciones de Windows. Si establece esta propiedad en un elemento de menú, ese elemento aparecerá en el extremo derecho y al final del menú. Se aplica a los elementos de nivel superior. Valor predeterminado: **False**.|  
|**Id.**|Un símbolo definido en el archivo de encabezado. Tipo: símbolo, entero o cadena entrecomillada. Puede usar cualquier símbolo de los que se encuentran disponibles normalmente en cualquier editor, aunque la [ventana Propiedades](/visualstudio/ide/reference/properties-window) no proporciona ninguna lista desplegable donde seleccionar.|  
|**Popup**|Si es True, el comando de menú es un menú emergente. Tipo: booleano. Valor predeterminado: True para los menús de nivel superior en una barra de menús. En caso contrario, es False.|  
|**Preguntar**|Contiene el texto que aparece en la barra de estado cuando se resalta el comando de menú. El texto se sitúa en la tabla de cadenas con el mismo identificador que el comando de menú. Esta propiedad se encuentra disponible para cualquier tipo de proyecto, pero la funcionalidad en tiempo de ejecución es específica de MFC.|  
|**Right to Left Justify**|Justifica a la derecha el comando de menú en la barra de menús, en tiempo de ejecución. Tipo: booleano. Valor predeterminado: False.|  
|**Right to Left Order**|Permite mostrar los comandos de menú de derecha a izquierda cuando la interfaz se localiza a idiomas con esta dirección de lectura, como el hebreo o el árabe.|  
|**Separador**|Si es True, el comando de menú es un separador. Tipo: booleano. Valor predeterminado: False.|  
  

  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editor de menús](../windows/menu-editor.md)