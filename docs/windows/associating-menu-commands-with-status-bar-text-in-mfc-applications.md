---
title: Asociar comandos de menú a texto de la barra de estado en aplicaciones MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars, associating menu items
- menus, status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d868c9270e23e2ee1fa0dcdc1845d9762cefb16c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649407"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>Asociar comandos de menú a texto de la barra de estado en aplicaciones MFC
La aplicación puede mostrar texto descriptivo para cada uno de los comandos de menú que puede seleccionar un usuario. Para ello, asigne una cadena de texto a cada comando de menú mediante el **Prompt** propiedad en el **propiedades** ventana. Si tiene una cadena en la [tabla de cadenas](../windows/string-editor.md) cuyo id. es igual que el comando, una aplicación MFC mostrará automáticamente este recurso de cadena en la barra de estado de la aplicación en ejecución cuando un usuario se desplace sobre un elemento de menú.  
  
### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>Para asociar un comando de menú a una cadena de texto de la barra de estado  
  
1.  En el editor de **menús** , seleccione el comando de menú.  
  
2.  En la [ventana Propiedades](/visualstudio/ide/reference/properties-window), escriba el texto de la barra de estado asociado en el cuadro **Prompt** .  
  
## <a name="requirements"></a>Requisitos  
 MFC  
  
## <a name="see-also"></a>Vea también  
 [Cadenas (ATL y MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Agregar comandos a un menú](../windows/adding-commands-to-a-menu.md)   
 [Editor de menús](../windows/menu-editor.md)