---
title: Agregar comandos a un menú (C++) | Microsoft Docs
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
- menus [C++], adding items
- commands [C++], adding to menus
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2c67242195f54f543bdc8c0c1be49fbed69fe91
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318725"
---
# <a name="adding-commands-to-a-menu-c"></a>Agregar comandos a un menú (C++)

### <a name="to-add-commands-to-a-menu"></a>Para agregar comandos a un menú

1. [Crear un menú](../windows/creating-a-menu.md).

2. Por ejemplo, haga clic en un nombre de menú, **archivo**.

   Cada menú se expandirá y expondrá un nuevo cuadro de elemento para los comandos. Por ejemplo, puede agregar los comandos **New**, **abierto**, y **cerrar** a un **archivo** menú.

3. En el nuevo cuadro de elemento, escriba un nombre para el nuevo comando de menú.

   > [!NOTE]
   > El texto que escriba aparecerá en el **Editor de menús** y en el cuadro **Leyenda** de la [ventana Propiedades](/visualstudio/ide/reference/properties-window). Puede editar las propiedades del nuevo menú en uno u otro componente.

   > [!TIP]
   > Puede definir una tecla nemotécnica (tecla de acceso rápido) que permita al usuario seleccionar el comando de menú. Escriba una y comercial (`&`) delante de una letra para especificarla como la tecla de acceso. El usuario puede seleccionar el comando de menú escribiendo esa letra.

4. En el **propiedades** ventana, seleccione el menú de comandos propiedades que se aplican. Para obtener más información, consulte [propiedades de comando de menú](../windows/menu-command-properties.md).

5. En el **símbolo del sistema** cuadro el **propiedades** ventana, escriba la cadena del mensaje que desea que aparezcan en la barra de estado de la aplicación.

   Esto crea una entrada en la tabla de cadenas con el mismo identificador de recursos que el comando de menú que creó.

   > [!NOTE]
   > Avisos solo afectan a los elementos de menú con un **emergente** propiedad de **True**. Por ejemplo, los elementos de menú de nivel superior pueden tener avisos si tienen elementos de submenú. El propósito de un **Prompt** es indicar lo que ocurrirá si un usuario hace clic en el elemento de menú.

6. Presione **ENTRAR** para completar el comando de menú.

   El cuadro de elemento nuevo se selecciona para que pueda crear comandos de menú adicionales.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de menús](../windows/menu-editor.md)  