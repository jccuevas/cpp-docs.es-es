---
title: "Agregar comandos a un menú | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.menu
dev_langs: C++
helpviewer_keywords:
- menu items, adding to menus
- menus, adding items
- commands, adding to menus
- commands
- menu items
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ccbfe6543854dc6a904d80c9e483dfde8122327a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="adding-commands-to-a-menu"></a>Agregar comandos a un menú
### <a name="to-add-commands-to-a-menu"></a>Para agregar comandos a un menú  
  
1.  [Crear un menú](../windows/creating-a-menu.md).  
  
2.  Haga clic en el nombre de un menú, como, por ejemplo, Archivo.  
  
     Cada menú se expandirá y expondrá un nuevo cuadro de elemento para los comandos. Por ejemplo, en un menú Archivo puede agregar los comandos Nuevo, Abrir y Cerrar.  
  
3.  En el nuevo cuadro de elemento, escriba un nombre para el nuevo comando de menú.  
  
    > [!NOTE]
    >  El texto que escriba aparecerá en el editor de menús y en el **título** cuadro el [ventana propiedades](/visualstudio/ide/reference/properties-window). Puede editar las propiedades del nuevo menú en uno u otro componente.  
  
    > [!TIP]
    >  Puede definir una tecla nemotécnica (tecla de acceso rápido) que permita al usuario seleccionar el comando de menú. Escriba una “y” comercial (&) delante de una letra para especificarla como la tecla nemotécnica. El usuario puede seleccionar el comando de menú escribiendo esa letra.  
  
4.  En la ventana Propiedades, seleccione las propiedades de comando de menú que sean aplicables. Para obtener más información, consulte [propiedades de comando de menú](../windows/menu-command-properties.md).  
  
5.  En el **símbolo del sistema** en la ventana Propiedades, escriba la cadena de mensaje que desea que aparezcan en la barra de estado de la aplicación.  
  
     Esto crea una entrada en la tabla de cadenas con el mismo identificador de recursos que el comando de menú que creó.  
  
    > [!NOTE]
    >  Los mensajes sólo afectan a los elementos de menú con un **emergente** propiedad de **True**. Por ejemplo, los elementos de menú de nivel superior pueden tener avisos si tienen elementos de submenú. El propósito de un aviso es indicar lo que sucederá si un usuario hace clic en el elemento de menú.  
  
6.  Presione **ENTRAR** para completar el comando de menú.  
  
     El cuadro de elemento nuevo se selecciona para que pueda crear comandos de menú adicionales.  
  

  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editor de menús](../windows/menu-editor.md)   
