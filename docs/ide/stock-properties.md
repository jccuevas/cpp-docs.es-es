---
title: "Propiedades estándar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- stock properties, about stock properties
- stock properties
ms.assetid: a89fc454-0b8e-447a-9033-4c8af46a24d9
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8712e75aad6eeaa50227989043a2aaad6973193d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="stock-properties"></a>Propiedades estándar
Si va a agregar una propiedad en una interfaz dispinterface MFC mediante el [Asistente para agregar propiedades](../ide/idl-attributes-add-property-wizard.md), puede elegir una propiedad estándar de la **nombre de la propiedad** lista en la [nombres](../ide/names-add-property-wizard.md) página de la Asistente. Estas propiedades son las siguientes:  
  
|Nombre de la propiedad|Descripción|  
|-------------------|-----------------|  
|**Apariencia**|Devuelve o establece un valor que determina la apariencia del control. El control **apariencia** propiedad puede incluir u omitir efectos tridimensionales. Se trata de una propiedad de ambiente de lectura/escritura.|  
|`BackColor`|Devuelve o establece el control ambiente `BackColor` propiedad a un color de paleta (RGB) o un color de sistema predefinidos. De forma predeterminada, su valor corresponde al color de primer plano del contenedor del control. Se trata de una propiedad de ambiente de lectura/escritura.|  
|`BorderStyle`|Devuelve o establece el estilo de borde para un control. Se trata de una propiedad de lectura/escritura.|  
|**Título**|Devuelve o establece el control **título** propiedad. El título es el título de la ventana. **Título** no tiene ningún **variable miembro** tipo de implementación.|  
|**Habilitado**|Devuelve o establece el control **habilitado** propiedad. Un control habilitado puede responder a eventos generados por el usuario.|  
|**Fuente**|Devuelve o establece la fuente del control ambiente. Es null si el control no tiene ninguna fuente.|  
|`ForeColor`|Devuelve o establece el control ambiente `ForeColor` propiedad.|  
|**hWnd**|Devuelve o establece el control **hWnd** propiedad. **hWnd** no tiene ningún **variable miembro** tipo de implementación.|  
|**ReadyState**|Devuelve o establece el control **ReadyState** propiedad. Puede ser un control no inicializado, inicializado, cargar, interactivo o completa. Vea [READYSTATE](https://msdn.microsoft.com/en-us/library/aa768362.aspx) en el *Internet SDK* para obtener más información.|  
|**Texto**|Devuelve o establece el texto contenido en un control. **Texto** no tiene ningún **variable miembro** tipo de implementación.|  
  
## <a name="see-also"></a>Vea también  
 [Agregar una propiedad](../ide/adding-a-property-visual-cpp.md)   
 [Atributos IDL, Asistente para agregar propiedades](../ide/idl-attributes-add-property-wizard.md)