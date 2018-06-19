---
title: 'Cómo: personalizar la barra de herramientas de acceso rápido | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0faa3a0fb66c4379824a6be190175b10e0415474
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349651"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Cómo: Personalizar la barra de herramientas de acceso rápido
La barra de herramientas de acceso rápido (QAT) es una barra de herramientas personalizable que contiene un conjunto de comandos que se muestran situada junto al botón de la aplicación o en las fichas de categoría. La siguiente ilustración muestra una barra de herramientas de acceso rápido típico.  
  
 ![Barra de herramientas de acceso rápido de MFC cinta](../mfc/media/quick_access_toolbar.png "quick_access_toolbar")  
  
 Para personalizar la barra de herramientas de acceso rápido, abrirlo en el **propiedades** ventana, modifique sus comandos y, a continuación, obtener una vista previa del control de la cinta de opciones.  
  
### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Para abrir la barra de herramientas de acceso rápido en la ventana Propiedades  
  
1.  En Visual Studio, en el **vista** menú, haga clic en **vista de recursos**.  
  
2.  En **vista de recursos**, haga doble clic en el recurso de cinta de opciones para mostrarla en la superficie de diseño.  
  
3.  En la superficie de diseño, haga clic en el menú de la barra de herramientas de acceso rápido y, a continuación, haga clic en **propiedades**.  
  
## <a name="quick-access-toolbar-properties"></a>Propiedades de la barra de herramientas de acceso rápido  
 En la tabla siguiente define las propiedades de la barra de herramientas de acceso rápido.  
  
|Property|de esquema JSON|  
|--------------|----------------|  
|Posición de QAT|Especifica la posición de la barra de herramientas de acceso rápido al iniciar la aplicación. La posición puede ser **anteriormente** o **a continuación** el control de la cinta de opciones.|  
|Elementos QAT|Especifica los comandos que están disponibles para la barra de herramientas de acceso rápido.|  
  
#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Para agregar o quitar comandos en la barra de herramientas de acceso rápido  
  
1.  En el **propiedades** ventana, haga clic en **QAT elementos**y, a continuación, haga clic en el botón de puntos suspensivos **(...)** .  
  
2.  En el **Editor de elementos de QAT** cuadro de diálogo, use la **agregar** y **quitar** botones para modificar la lista de comandos en la barra de herramientas de acceso rápido.  
  
3.  Si desea que un comando que aparecerá en la barra de herramientas de acceso rápido y el menú de la barra de herramientas de acceso rápido, active la casilla situada junto al comando. Si desea que el comando aparezca sólo en el menú, desactive la casilla.  
  
## <a name="previewing-the-ribbon"></a>Obtener una vista previa de la cinta de opciones  
 Comandos de barra de herramientas de acceso rápidos no aparecen en la superficie de diseño. Para verlas, debe obtener una vista previa de la cinta de opciones o ejecutar la aplicación.  
  
#### <a name="to-preview-the-ribbon-control"></a>Para obtener una vista previa del control de la cinta de opciones  
  
-   En el **barra de herramientas del Editor de Ribbon**, haga clic en **Ribbon de prueba**.  
  
## <a name="see-also"></a>Vea también  
 [Diseñador de la cinta de opciones (MFC)](../mfc/ribbon-designer-mfc.md)

