---
title: 'Cómo: Personalizar la barra de herramientas de acceso rápido'
ms.date: 09/07/2019
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
ms.openlocfilehash: 5d168fc395e27eea3705fc8e69c88569ecb0f7ee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620029"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Cómo: Personalizar la barra de herramientas de acceso rápido

La barra de herramientas de acceso rápido (QAT) es una barra de herramientas personalizable que contiene un conjunto de comandos que se muestran junto al botón aplicación o en las pestañas categoría. En la ilustración siguiente se muestra una barra de herramientas de acceso rápido típica.

![Barra de herramientas de acceso rápido de la cinta de opciones de MFC](../mfc/media/quick_access_toolbar.png "Barra de herramientas de acceso rápido de la cinta de opciones de MFC")

Para personalizar la barra de herramientas de acceso rápido, ábrala en la ventana **propiedades** , modifique sus comandos y, a continuación, obtenga una vista previa del control de la cinta de opciones.

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Para abrir la barra de herramientas de acceso rápido en el ventana Propiedades

1. En Visual Studio, en el menú **Ver** , haga clic en **vista de recursos**.

1. En **vista de recursos**, haga doble clic en el recurso de la cinta de opciones para mostrarlo en la superficie de diseño.

1. En la superficie de diseño, haga clic con el botón secundario en el menú de la barra de herramientas acceso rápido y haga clic en **propiedades**.

## <a name="quick-access-toolbar-properties"></a>Propiedades de la barra de herramientas de acceso rápido

En la tabla siguiente se definen las propiedades de la barra de herramientas de acceso rápido.

|Propiedad|Definición|
|--------------|----------------|
|Posición QAT|Especifica la posición de la barra de herramientas de acceso rápido cuando se inicia la aplicación. La posición puede estar **por encima** o **por debajo** del control de la cinta de opciones.|
|Elementos QAT|Especifica los comandos que están disponibles para la barra de herramientas de acceso rápido.|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Para agregar o quitar comandos en la barra de herramientas de acceso rápido

1. En la ventana **propiedades** , haga clic en **Qat elementos**y, a continuación, haga clic en el botón de puntos suspensivos **(...)**.

1. En el cuadro de diálogo **Editor de elementos de Qat** , use los botones **Agregar** y **quitar** para modificar la lista de comandos de la barra de herramientas de acceso rápido.

1. Si desea que aparezca un comando en la barra de herramientas de acceso rápido y en el menú de la barra de herramientas de acceso rápido, active la casilla situada junto al comando. Si desea que el comando solo aparezca en el menú, desactive la casilla.

## <a name="previewing-the-ribbon"></a>Obtener una vista previa de la cinta de opciones

Los comandos de la barra de herramientas de acceso rápido no aparecen en la superficie de diseño. Para verlos, debe obtener una vista previa de la cinta de opciones o ejecutar la aplicación.

#### <a name="to-preview-the-ribbon-control"></a>Para obtener una vista previa del control Ribbon

- En la **barra de herramientas del editor**de la cinta de opciones, haga clic en **probar cinta**.

## <a name="see-also"></a>Consulte también

[Diseñador de la cinta de opciones (MFC)](ribbon-designer-mfc.md)
