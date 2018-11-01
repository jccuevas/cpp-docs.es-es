---
title: Asociar comandos de menú a texto de la barra de estado en aplicaciones MFC
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [C++], associating menu items
- menus [C++], status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
ms.openlocfilehash: fc39695358a9c1f2f62878487a5e4fedf5db2b82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468892"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>Asociar comandos de menú a texto de la barra de estado en aplicaciones MFC

La aplicación de MFC puede mostrar texto descriptivo para cada uno de los comandos de menú, que puede seleccionar un usuario. Para ello, asigne una cadena de texto a cada comando de menú mediante el **Prompt** propiedad en el **propiedades** ventana. Si tiene una cadena en la [tabla de cadenas](../windows/string-editor.md) cuyo id. es igual que el comando, una aplicación MFC mostrará automáticamente este recurso de cadena en la barra de estado de la aplicación en ejecución cuando un usuario se desplace sobre un elemento de menú.

### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>Para asociar un comando de menú a una cadena de texto de la barra de estado

1. En el editor de **menús** , seleccione el comando de menú.

2. En la [ventana Propiedades](/visualstudio/ide/reference/properties-window), escriba el texto de la barra de estado asociado en el cuadro **Prompt** .

## <a name="requirements"></a>Requisitos

MFC

## <a name="see-also"></a>Vea también

[Cadenas (ATL y MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Adición de comandos a un menú](../windows/adding-commands-to-a-menu.md)<br/>
[Editor de menús](../windows/menu-editor.md)