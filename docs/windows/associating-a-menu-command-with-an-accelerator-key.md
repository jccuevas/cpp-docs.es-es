---
title: "Asociar un comando de menú a una tecla de aceleración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keyboard shortcuts, menu association
- commands, associating menu commands with accelerator keys
- menu commands, associating with keyboard shortcuts
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 79a16cf8d67fb7a6a45043c28455a7ed22f90ffa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="associating-a-menu-command-with-an-accelerator-key"></a>Asociar un comando de menú a una tecla de aceleración
A menudo quiere que un elemento de menú u una combinación de teclado ejecuten el mismo comando de programa. Para ello, use el editor de menús para asignar el mismo identificador de recurso al comando de menú y a una entrada de la tabla de aceleradores de la aplicación. A continuación, edite el [Título](../windows/menu-command-properties.md) del comando de menú para que muestre el nombre del acelerador.  
  
### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Para asociar un comando de menú a una tecla de aceleración  
  
1.  En el editor de **menús** , seleccione el comando de menú que quiere.  
  
2.  En la [Ventana Propiedades](/visualstudio/ide/reference/properties-window), agregue el nombre de la tecla de aceleración a la propiedad **Título** :  
  
    -   Tras el título del menú, escriba la secuencia de escape de una tabulación (\t), para que todas las teclas de aceleración del menú quedan alineadas.  
  
    -   Escriba el nombre de la tecla modificadora (**CTRL**, **ALT**o **MAYÚS**) seguida de un signo más (**+**) y el nombre, la letra o el símbolo de la tecla adicional.  
  
         Por ejemplo, para asignar **CTRL+A** al comando **Abrir** del menú **Archivo** , modifique el **Título** del comando de menú para que tenga el siguiente aspecto:  
  
        ```  
        &Open...\tCtrl+O   
        ```  
  
         El comando de menú en el editor de menús se actualiza para reflejar el nuevo título conforme se escribe.  
  
3.  [Cree la entrada de la tabla de aceleradores](../windows/adding-an-entry-to-an-accelerator-table.md) en el editor **Acelerador** y asígnele el mismo identificador que el comando de menú. Use una combinación de teclas que le resulte sencilla de recordar.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Agregar comandos a un menú](../windows/adding-commands-to-a-menu.md)   
 [Editor de menús](../windows/menu-editor.md)