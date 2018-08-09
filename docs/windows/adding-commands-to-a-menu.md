---
title: Agregar comandos a un menú | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.menu
dev_langs:
- C++
helpviewer_keywords:
- menu items, adding to menus
- menus, adding items
- commands, adding to menus
- commands
- menu items
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0c744e920c71b74d9296e6961add704435658fe
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644734"
---
# <a name="adding-commands-to-a-menu"></a>Agregar comandos a un menú
### <a name="to-add-commands-to-a-menu"></a>Para agregar comandos a un menú  
  
1.  [Crear un menú](../windows/creating-a-menu.md).  
  
2.  Por ejemplo, haga clic en un nombre de menú, **archivo**.  
  
     Cada menú se expandirá y expondrá un nuevo cuadro de elemento para los comandos. Por ejemplo, puede agregar los comandos **New**, **abierto**, y **cerrar** a un **archivo** menú.  
  
3.  En el nuevo cuadro de elemento, escriba un nombre para el nuevo comando de menú.  
  
    > [!NOTE]
    >  El texto que escriba aparecerá en el **Editor de menús** y en el cuadro **Leyenda** de la [ventana Propiedades](/visualstudio/ide/reference/properties-window). Puede editar las propiedades del nuevo menú en uno u otro componente.  
  
    > [!TIP]
    >  Puede definir una tecla nemotécnica (tecla de acceso rápido) que permita al usuario seleccionar el comando de menú. Escriba una y comercial (`&`) delante de una letra para especificarla como la tecla de acceso. El usuario puede seleccionar el comando de menú escribiendo esa letra.  
  
4.  En el **propiedades** ventana, seleccione el menú de comandos propiedades que se aplican. Para obtener más información, consulte [propiedades de comando de menú](../windows/menu-command-properties.md).  
  
5.  En el **símbolo del sistema** cuadro el **propiedades** ventana, escriba la cadena del mensaje que desea que aparezcan en la barra de estado de la aplicación.  
  
     Esto crea una entrada en la tabla de cadenas con el mismo identificador de recursos que el comando de menú que creó.  
  
    > [!NOTE]
    >  Avisos solo afectan a los elementos de menú con un **emergente** propiedad de **True**. Por ejemplo, los elementos de menú de nivel superior pueden tener avisos si tienen elementos de submenú. El propósito de un **Prompt** es indicar lo que ocurrirá si un usuario hace clic en el elemento de menú.  
  
6.  Presione **ENTRAR** para completar el comando de menú.  
  
     El cuadro de elemento nuevo se selecciona para que pueda crear comandos de menú adicionales.  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editor de menús](../windows/menu-editor.md)   