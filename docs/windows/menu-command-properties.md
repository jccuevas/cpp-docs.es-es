---
title: Propiedades de comando de menú (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menu items, properties
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c846cecb415365db92e3097bbf04ab06cd4209d0
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860451"
---
# <a name="menu-command-properties-c"></a>Propiedades de comando de menú (C++)

La siguiente información se organiza según el **menú** propiedades que aparecen en la [ventana propiedades](/visualstudio/ide/reference/properties-window) cuando se selecciona un comando de menú. Están ordenadas alfabéticamente, aunque el **propiedades** ventana también le permite ver estas propiedades por categoría.

|Property|Descripción|
|--------------|-----------------|
|**Break**|Puede ser uno de estos valores:<br /><br />- **Ninguno** (predeterminado): sin interrupción.<br />- **Columna**: en los menús estáticos, este valor sitúa el comando de menú en una nueva línea. En los menús emergentes, este valor sitúa el comando de menú en una columna nueva, sin línea divisoria entre las columnas. Esta propiedad solo afecta a la apariencia del menú en tiempo de ejecución, no en el editor de menús.<br />- **Barra**: igual que **columna** , excepto en los menús emergentes, este valor separa la nueva columna de la columna antigua con una línea vertical. Esta propiedad afecta a la apariencia del menú en tiempo de ejecución, no en el **menú** editor.|
|**Título**|El texto que etiqueta el comando de menú (el nombre del menú). Para convertir una de las letras del título de un comando de menú en la tecla de acceso, sitúe delante de ella una Y comercial (&).|
|**Activadas**|Si **True**, el comando de menú se activa inicialmente. Tipo: **Bool**. Valor predeterminado: **False**.|
|**Habilitado**|Si es **False**, se deshabilita el elemento de menú.|
|**Grayed**|Si **True**, el comando de menú inicialmente está atenuado e inactivo. Tipo: **Bool**. Valor predeterminado: **False**.|
|**Ayuda**|Alinea el elemento de menú a la derecha. Por ejemplo, el comando de menú **Ayuda** siempre está a la derecha en todas las aplicaciones de Windows. Si establece esta propiedad en un elemento de menú, ese elemento aparecerá en el extremo derecho y al final del menú. Se aplica a los elementos de nivel superior. Valor predeterminado: **False**.|
|**Id.**|Un símbolo definido en el archivo de encabezado. Tipo: **símbolo**, **entero**, o **cadena entrecomillada**. Puede usar cualquier símbolo de los que se encuentran disponibles normalmente en cualquier editor, aunque la [ventana Propiedades](/visualstudio/ide/reference/properties-window) no proporciona ninguna lista desplegable donde seleccionar.|
|**Popup**|Si **True**, el comando de menú es un menú emergente. Tipo: **Bool**. Valor predeterminado: **True** para menús de nivel superior en un menú de la barra; en caso contrario **False**.|
|**Preguntar**|Contiene el texto que aparece en la barra de estado cuando se resalta el comando de menú. El texto se sitúa en la tabla de cadenas con el mismo identificador que el comando de menú. Esta propiedad se encuentra disponible para cualquier tipo de proyecto, pero la funcionalidad en tiempo de ejecución es específica de MFC.|
|**Right to Left Justify**|Justifica a la derecha el comando de menú en la barra de menús, en tiempo de ejecución. Tipo: **Bool**. Valor predeterminado: **False**.|
|**Right to Left Order**|Permite mostrar los comandos de menú de derecha a izquierda cuando la interfaz se localiza a idiomas con esta dirección de lectura, como el hebreo o el árabe.|
|**Separator**|Si **True**, el comando de menú es un separador. Tipo: **Bool**. Valor predeterminado: **False**.|

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de menús](../windows/menu-editor.md)