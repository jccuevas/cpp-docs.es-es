---
title: 'Cómo: personalizar la barra de herramientas acceso rápido | Microsoft Docs'
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
ms.openlocfilehash: 0f3ec14971b69788892690c26ef2759f3b35d55f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419111"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Cómo: Personalizar la barra de herramientas de acceso rápido

La barra de herramientas de acceso rápido (QAT) es una barra de herramientas personalizable que contiene un conjunto de comandos que se muestran al lado del botón de la aplicación o en las fichas de categoría. La siguiente ilustración muestra una barra de herramientas de acceso rápido típico.

![Barra de herramientas de acceso rápido de MFC Ribbon](../mfc/media/quick_access_toolbar.png "quick_access_toolbar")

Para personalizar la barra de herramientas de acceso rápido, ábralo en el **propiedades** , modifique sus comandos y, a continuación, obtener una vista previa del control de la cinta de opciones.

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Para abrir la barra de herramientas de acceso rápido en la ventana Propiedades

1. En Visual Studio, en el **vista** menú, haga clic en **vista de recursos**.

1. En **vista de recursos**, haga doble clic en el recurso de cinta para que se muestre en la superficie de diseño.

1. En la superficie de diseño, haga clic en el menú de la barra de herramientas de acceso rápido y, a continuación, haga clic en **propiedades**.

## <a name="quick-access-toolbar-properties"></a>Propiedades de la barra de herramientas de acceso rápido

En la tabla siguiente define las propiedades de la barra de herramientas de acceso rápido.

|Property|de esquema JSON|
|--------------|----------------|
|Posición de QAT|Especifica la posición de la barra de herramientas de acceso rápido al iniciar la aplicación. La posición puede ser **anteriormente** o **debajo** el control de la cinta de opciones.|
|Elementos QAT|Especifica los comandos que están disponibles para la barra de herramientas de acceso rápido.|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Para agregar o quitar comandos en la barra de herramientas de acceso rápido

1. En el **propiedades** ventana, haga clic en **QAT Items**y, a continuación, haga clic en el botón de puntos suspensivos **(...)** .

1. En el **Editor de elementos de QAT** cuadro de diálogo, use el **agregar** y **quitar** botones para modificar la lista de comandos en la barra de herramientas de acceso rápido.

1. Si desea que un comando aparezca en la barra de herramientas de acceso rápido y el menú de la barra de herramientas de acceso rápido, active la casilla situada junto al comando. Si desea que el comando aparezca sólo en el menú, desactive la casilla.

## <a name="previewing-the-ribbon"></a>Vista previa de la cinta de opciones

Comandos de barra de herramientas acceso rápidos no aparecen en la superficie de diseño. Para verlos, debe obtener una vista previa de la cinta de opciones o ejecutar la aplicación.

#### <a name="to-preview-the-ribbon-control"></a>Para obtener una vista previa del control de la cinta de opciones

- En el **barra de herramientas del Editor de Ribbon**, haga clic en **Ribbon de prueba**.

## <a name="see-also"></a>Vea también

[Diseñador de la cinta de opciones (MFC)](../mfc/ribbon-designer-mfc.md)

