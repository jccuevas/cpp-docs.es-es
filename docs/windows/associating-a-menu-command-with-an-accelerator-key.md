---
title: Asociar un comando de menú a una tecla de aceleración | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts, menu association
- commands, associating menu commands with accelerator keys
- menu commands, associating with keyboard shortcuts
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e4b1665e54a03bf7d5f4705aaa3d76962ed16a0
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649977"
---
# <a name="associating-a-menu-command-with-an-accelerator-key"></a>Asociar un comando de menú a una tecla de aceleración
A menudo quiere que un elemento de menú u una combinación de teclado ejecuten el mismo comando de programa. Para ello, uso el **menú** editor para asignar el mismo identificador de recurso para el comando de menú y a una entrada en la tabla de aceleradores de la aplicación. A continuación, edite el [Título](../windows/menu-command-properties.md) del comando de menú para que muestre el nombre del acelerador.  
  
### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Para asociar un comando de menú a una tecla de aceleración  
  
1.  En el editor de **menús** , seleccione el comando de menú que quiere.  
  
2.  En la [Ventana Propiedades](/visualstudio/ide/reference/properties-window), agregue el nombre de la tecla de aceleración a la propiedad **Título** :  
  
    -   Tras el título del menú, escriba la secuencia de escape de una tabulación (\t), para que todas las teclas de aceleración del menú quedan alineadas.  
  
    -   Escriba el nombre de la tecla modificadora (**Ctrl**, **Alt**, o **MAYÚS**) seguido por un signo más (**+**) y el nombre, la carta, o símbolo de la tecla adicional.  
  
         Por ejemplo, para asignar **Ctrl**+**O** a la **abierto** comando el **archivo** menú, modifique el comando de menú  **Título** por lo que se parezca a esto:  
  
        ```  
        &Open...\tCtrl+O   
        ```  
  
         El comando de menú en el **menú** editor se actualiza para reflejar el nuevo título a medida que lo escribe.  
  
3.  [Cree la entrada de la tabla de aceleradores](../windows/adding-an-entry-to-an-accelerator-table.md) en el editor **Acelerador** y asígnele el mismo identificador que el comando de menú. Use una combinación de teclas que le resulte sencilla de recordar.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Agregar comandos a un menú](../windows/adding-commands-to-a-menu.md)   
 [Editor de menús](../windows/menu-editor.md)