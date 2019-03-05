---
title: Procedimiento Convertir una cinta MFC existente en un recurso de cinta
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
ms.openlocfilehash: b4265a7bf3ebe2c4926f21572d802b75bd525990
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295494"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Filtrar Convertir una cinta MFC existente en un recurso de cinta

Recursos de la cinta de opciones son más fáciles de visualizar, modificar y mantener que las cintas de opciones codificada de forma manual. Este tema describe cómo convertir una cinta de opciones codificada de forma manual en un proyecto MFC en un recurso de cinta.

Debe tener un proyecto MFC existente que tiene código que utiliza las clases de cinta de opciones MFC, por ejemplo, [CMFCRibbonBar (clase)](../mfc/reference/cmfcribbonbar-class.md).

### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>Para convertir una cinta de MFC en un recurso de cinta

1. En Visual Studio, en un proyecto MFC existente, abra el archivo de código fuente donde el `CMFCRibbonBar` se inicializa el objeto. Normalmente, el archivo es mainfrm.cpp. Agregue el código siguiente después del código de inicialización de la cinta de opciones.

```
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");
```

   Guarde y cierre el archivo.

1. Compilar y ejecutar la aplicación MFC y, a continuación, en el Bloc de notas, abra RibbonOutput.txt y copie su contenido.

1. En Visual Studio, en el **proyecto** menú, haga clic en **Agregar recurso**. En el **Agregar recurso** cuadro de diálogo, seleccione **cinta** y, a continuación, haga clic en **New**.

   Visual Studio crea un recurso de cinta y lo abre en la vista Diseño. El identificador de recurso de cinta es IDR_RIBBON1, que se muestra en **vista de recursos**. La cinta de opciones se define en el archivo XML de ribbon1.mfcribbon ms.

1. En Visual Studio, abra ribbon1.mfcribbon ms, elimine su contenido y, a continuación, pegue el contenido de RibbonOutput.txt, que copió anteriormente. Guarde y cierre ribbon1.mfcribbon ms.

1. Vuelva a abrir el archivo de código fuente donde se inicializa el objeto CMFCRibbonBar (normalmente, mainfrm.cpp) y marque como comentario existente código de la cinta de opciones. Agregue el código siguiente después del código que se hayan anulado.

```
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
```

1. Compile el proyecto y ejecute el programa.

## <a name="see-also"></a>Vea también

[Diseñador de la cinta de opciones (MFC)](../mfc/ribbon-designer-mfc.md)
