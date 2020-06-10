---
title: 'Cómo: Convertir una cinta de MFC existente en un recurso de cinta'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
ms.openlocfilehash: 56f36c977453d338b9e9bbd2462c1a8830ffe258
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620047"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Cómo: Convertir una cinta de MFC existente en un recurso de cinta

Los recursos de la cinta son más fáciles de visualizar, modificar y mantener que las cintas de opciones codificadas manualmente. En este tema se describe cómo convertir una cinta codificada manualmente en un proyecto MFC en un recurso de la cinta de opciones.

Debe tener un proyecto MFC existente que tenga código que use las clases de la cinta de opciones de MFC, por ejemplo, la [clase CMFCRibbonBar](reference/cmfcribbonbar-class.md).

### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>Para convertir una cinta de MFC en un recurso de cinta de opciones

1. En Visual Studio, en un proyecto de MFC existente, abra el archivo de código fuente donde `CMFCRibbonBar` se inicializa el objeto. Normalmente, el archivo es MainFrm. cpp. Agregue el código siguiente después del código de inicialización de la cinta de opciones.

```
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");
```

   Guarde y cierre el archivo.

1. Compile y ejecute la aplicación MFC y, a continuación, en el Bloc de notas, abra RibbonOutput. txt y copie su contenido.

1. En Visual Studio, en el menú **proyecto** , haga clic en **Agregar recurso**. En el cuadro de diálogo **Agregar recurso** , seleccione **cinta** de opciones y, a continuación, haga clic en **nuevo**.

   Visual Studio crea un recurso de cinta de opciones y lo abre en la vista Diseño. El identificador de recurso de la cinta de opciones es IDR_RIBBON1, que se muestra en **vista de recursos**. La cinta de opciones se define en el archivo Ribbon1. mfcribbon-MS XML.

1. En Visual Studio, abra Ribbon1. mfcribbon-MS, elimine su contenido y, a continuación, pegue el contenido de RibbonOutput. txt, que copió anteriormente. Guarde y cierre Ribbon1. mfcribbon-ms.

1. Abra de nuevo el archivo de código fuente donde se inicializa el objeto CMFCRibbonBar (normalmente, MainFrm. cpp) y comente el código existente de la cinta de opciones. Agregue el código siguiente después del código que ha comentado.

```
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
```

1. Compile el proyecto y ejecute el programa.

## <a name="see-also"></a>Consulte también

[Diseñador de la cinta de opciones (MFC)](ribbon-designer-mfc.md)
